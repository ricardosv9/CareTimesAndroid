# CareTimesAndroid
# 📱 CareTimes - App Android para Gestión de Citas Médicas

**CareTimes** es una aplicación Android diseñada para facilitar la gestión de citas médicas entre pacientes y doctores. La app permite a los usuarios registrarse, iniciar sesión, gestionar su perfil, solicitar nuevas citas, visualizar las programadas y cancelarlas desde cualquier dispositivo móvil.

Este cliente Android se comunica con un servidor REST desarrollado en Java/Spring Boot, el cual interactúa con una base de datos PostgreSQL para asegurar la persistencia de los datos.

---

## 🚀 Tecnologías utilizadas

- Android Studio
- Java
- Retrofit2 (consumo de API REST)
- Gson (serialización JSON)
- Patrón MVC y Singleton
- Intents para navegación
- PostgreSQL (en el backend)

---

## ✨ Funcionalidades

### Para pacientes:
- Registro e inicio de sesión
- Edición de perfil (nombre, contraseña, sexo, altura, peso, nacionalidad)
- Creación de nuevas citas médicas (selección por especialidad, fecha y hora)
- Visualización de citas futuras
- Cancelación de citas existentes
- Cierre de sesión

### Para doctores:
- Inicio de sesión
- Edición de perfil
- Visualización y cancelación de citas asignadas

---

## 📱 Flujo y navegación

LoginActivity
│
├──> RegistroActivity
│
└──> MainPacienteActivity ──> PerfilPacienteActivity
├──> AppointmentsListActivity
└──> NewAppointmentActivity

MainDoctorActivity ──> PerfilPacienteActivity
└──> AppointmentsListActivity

- Las actividades usan **Intents explícitos** para navegación.
- El estado de usuario (nombre y rol) se pasa entre pantallas mediante `Intent extras`.
- El botón de cierre de sesión borra las credenciales y reinicia el stack de navegación.

---

## 🔌 Conexión con el servidor

- Toda la comunicación se realiza a través de **Retrofit2**.
- La clase `ApiClient` implementa el patrón Singleton para mantener una única instancia de Retrofit.
- `ApiService` define todos los endpoints necesarios para:
  - Login y registro
  - Obtener y actualizar perfil
  - CRUD de citas médicas

### URL base en emulador

`java`
private static final String BASE_URL = "http://10.0.2.2:8080/api/";


### Estructura del proyecto
app/
├── activities/             // Login, Main, Perfil, Citas, Nueva Cita
├── models/                // Clases: User, MedicalAppointment
├── network/               // ApiClient, ApiService, LoginResponse
└── res/layout/            // Archivos XML de UI

### Instalación y ejecución
git clone https://github.com/tuusuario/CareTimesAndroid.git

