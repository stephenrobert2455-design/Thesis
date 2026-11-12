# MediGuide BD — Healthcare Website Prototype

A responsive front-end demo based on the requested four modules:
- Patient website: symptom guidance, doctor/hospital search, appointment request, appointment history.
- Doctor dashboard: appointment list, accept/reject actions, availability toggle.
- Admin dashboard: directory overview and appointment monitoring.
- Symptom checker: rule-based specialty suggestions (not a medical diagnosis).

## Run the project
1. Extract `MediGuide-BD.zip`.
2. Open the `MediGuide-BD` folder.
3. Double-click `index.html`, or run a local server:
   - VS Code: install Live Server and choose **Open with Live Server**.
   - Python: `python -m http.server 8000`, then visit `http://localhost:8000`.

No build step or package installation is required.

## Demo behavior
- Use **Log in** to switch between Patient, Doctor, and Admin demo workspaces.
- Submit an appointment request from a doctor card.
- The request appears in the Patient and Doctor dashboards.
- Accept or reject it in the Doctor dashboard; the status updates in the other dashboards.
- Appointment data is stored in this browser's `localStorage`.

## Important: prototype vs production
This ZIP is a working front-end prototype, not a deployed production healthcare service. It currently uses sample doctor/hospital data and browser-local demo storage. It does not include:
- Laravel/PHP server, MySQL database, migrations, or API endpoints.
- Real user registration, secure login, role-based server authorization, or password handling.
- A connected AI/LLM symptom analysis API or clinically validated triage logic.
- Verified live doctor schedules, hospital data, or actual appointment delivery.
- Medical-record encryption, audit logs, consent management, or production privacy/security controls.

The symptom checker only suggests a possible medical specialty based on selected symptoms. It does not diagnose. For severe or sudden symptoms, users should seek urgent medical care.

## Suggested Laravel + MySQL production architecture
- `users` (role: patient/doctor/admin), `patients`, `doctors`, `hospitals`
- `specialties`, `doctor_hospital`, `doctor_schedules`
- `appointments` (patient_id, doctor_id, hospital_id, appointment_at, status, reason)
- `medical_records` (patient_id, record_type, file_path, notes, access permissions)
- Laravel authentication, policies/gates, validation, CSRF protection, secure file storage, audit logs
- Symptom guidance API isolated behind a server endpoint; do not expose API keys in browser JavaScript.

## Customize sample data
Edit the `doctors` and `hospitals` arrays near the top of `assets/js/app.js`.
