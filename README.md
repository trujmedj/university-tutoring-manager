# University Tutoring Management System

Desktop application for managing the academic tutoring programme of a university. A coordinator assigns tutors to students automatically, tutors follow up on their students and raise alerts, and students and tutors can talk through a built-in chat.

Built with **C++** and **Qt 6**, with a **MariaDB** database, as a team project for the Software Engineering course of the Computer Engineering degree at the University of Córdoba.

![Main window](docs/screenshot-main.png)

## Features

The application has three user roles, each with its own window after logging in.

**Coordinator**
- Automatically assigns tutors to students without one, matching each student's degree with the tutor's department and respecting each tutor's maximum number of students
- Filters the assignment by faculty and shows a preview before confirming it
- Reviews and closes the alerts raised by tutors
- Resets all assignments to start again

**Tutor**
- Sees the list of assigned students
- Raises alerts about a student, which are sent to the coordinator
- Chats with each of their students

**Student**
- Sees their assigned tutor
- Chats with their tutor

## Testing

The project includes unit tests written with **Qt Test**:

- `TestAsignacion`: tutor capacity and degree/department matching
- `TestAlertas`: database connection and alerts table
- `TestChat`: sending and reading chat messages

## Tech stack

C++17 · Qt 6 (Widgets, SQL, Test) · Qt Designer · MariaDB · qmake

## Getting started

These steps are for Ubuntu/Debian.

1. Install Qt 6, MariaDB and the Qt driver for MariaDB/MySQL:
   ```bash
   sudo apt install qt6-base-dev libqt6sql6-mysql mariadb-server
   ```
2. Create the database and a local user (the application connects as `admin` with password `pepe`, for local development only):
   ```bash
   sudo mysql -e "CREATE DATABASE gestion_tutorias; CREATE USER 'admin'@'localhost' IDENTIFIED BY 'pepe'; GRANT ALL ON gestion_tutorias.* TO 'admin'@'localhost';"
   sudo mysql gestion_tutorias < base_datos_completa.sql
   ```
3. Open `GestionTutorias.pro` in **Qt Creator** and run it, or build it from the terminal:
   ```bash
   qmake6 GestionTutorias.pro
   make
   ./GestionTutorias
   ```

### Demo users

| Role | Email | Password |
|---|---|---|
| Coordinator | `admin@uco.es` | `admin` |
| Tutor | `turing@uco.es` | `1234` |
| Student | `aaron@uco.es` | `1234` |

All the users in the sample data are fictional.

## Team

Developed as a team project by José Trujillo Medina, Antonio and Carlos.
