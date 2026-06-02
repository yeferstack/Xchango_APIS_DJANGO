# API REST - Usuario Seguridad
API CRUD desarrollada con Django REST Framework para la gestión del esquema `Usuario_seguridad` en la base de datos `Xchango_db`.

---

## Tecnologías utilizadas
- Python 3.12
- Django 6.0
- Django REST Framework
- PostgreSQL
- psycopg2
- python-decouple

---

## Estructura del proyecto
```
usuario_seguridad_django/
├── .env
├── .gitignore
├── manage.py
├── run.py
├── backend/
│   ├── settings.py
│   ├── urls.py
│   ├── wsgi.py
│   └── asgi.py
└── api/
    ├── models.py
    ├── serializers.py
    ├── views.py
    ├── urls.py
    ├── admin.py
    └── migrations/
```

---

## Base de datos
- **Base de datos:** `Xchango_db`
- **Esquema:** `Usuario_seguridad`

### Tablas
| Tabla | Descripción |
|---|---|
| `Usuario` | Datos principales del usuario (correo, estado, verificación) |
| `Credenciales` | Hash de contraseña, intentos fallidos y bloqueo |
| `Crear_contrasena` | Registro temporal de creación de contraseña |
| `HistorialContrasena` | Historial de contraseñas anteriores del usuario |
| `RecuperacionContrasena` | Tokens y códigos para recuperación de contraseña |
| `Sesion` | Sesiones activas con token, IP y user agent |
| `IntentoLogin` | Registro de intentos de inicio de sesión |
| `Perfil` | Datos personales del usuario (nombre, teléfono, municipio, etc.) |

---

## Instalación y ejecución

```bash
# 1. Activar el entorno virtual
venv\Scripts\activate

# 2. Instalar dependencias
pip install django djangorestframework drf-yasg psycopg2-binary python-decouple

# 3. Aplicar migraciones
python manage.py migrate

# 4. Correr el servidor
python run.py
```

---

## Endpoints disponibles

Base URL: `http://127.0.0.1:9000/api/`

| Método | Endpoint | Descripción |
|---|---|---|
| GET / POST | `/api/usuarios/` | Listar o crear usuarios |
| GET / PUT / DELETE | `/api/usuarios/{id}/` | Detalle, editar o eliminar un usuario |
| GET / POST | `/api/credenciales/` | Listar o crear credenciales |
| GET / PUT / DELETE | `/api/credenciales/{id}/` | Detalle, editar o eliminar credenciales |
| GET / POST | `/api/crear-contrasena/` | Listar o crear registro de contraseña |
| GET / PUT / DELETE | `/api/crear-contrasena/{id}/` | Detalle, editar o eliminar |
| GET / POST | `/api/historial-contrasena/` | Listar o crear historial |
| GET / PUT / DELETE | `/api/historial-contrasena/{id}/` | Detalle, editar o eliminar |
| GET / POST | `/api/recuperacion-contrasena/` | Listar o crear recuperación |
| GET / PUT / DELETE | `/api/recuperacion-contrasena/{id}/` | Detalle, editar o eliminar |
| GET / POST | `/api/sesiones/` | Listar o crear sesiones |
| GET / PUT / DELETE | `/api/sesiones/{id}/` | Detalle, editar o eliminar |
| GET / POST | `/api/intentos-login/` | Listar o crear intentos de login |
| GET / PUT / DELETE | `/api/intentos-login/{id}/` | Detalle, editar o eliminar |
| GET / POST | `/api/perfiles/` | Listar o crear perfiles |
| GET / PUT / DELETE | `/api/perfiles/{id}/` | Detalle, editar o eliminar |



# Xchango API — Módulo Publicaciones

API REST CRUD para el módulo de publicaciones del sistema **Xchango**, desarrollada en **Django 6 + Django REST Framework + PostgreSQL**.

---

## Tecnologías

| Paquete | Versión |
|---|---|
| Python | 3.14 |
| Django | 6.0.5 |
| djangorestframework | 3.17.1 |
| drf-yasg | 1.21.15 |
| psycopg2-binary | 2.9.12 |
| python-decouple | 3.x |

---

## Estructura del proyecto

```
xchango_publicaciones/
├── .env                    ← Variables de entorno (NO subir al repo)
├── .gitignore
├── manage.py
├── run.py                  ← Shortcut para correr el servidor
├── backen/
│   ├── __init__.py
│   ├── settings.py         ← Configuración del proyecto
│   ├── urls.py             ← Rutas raíz + Swagger
│   ├── asgi.py
│   └── wsgi.py
└── api/
    ├── __init__.py
    ├── apps.py
    ├── models.py           ← 8 modelos del schema 'Publicaciones'
    ├── serializers.py      ← Serializers de cada modelo
    ├── views.py            ← ViewSets CRUD
    ├── urls.py             ← Router con los 8 recursos
    ├── admin.py
    ├── tests.py
    └── migrations/
        └── __init__.py
```

---

## Instalación

```bash
# 1. Crear entorno virtual
python -m venv venv

# 2. Activar entorno virtual (Windows)
venv\Scripts\activate.bat

# 3. Instalar dependencias
pip install django djangorestframework psycopg2-binary drf-yasg python-decouple setuptools
```

## Correr el servidor

```bash
python run.py
```

El servidor inicia en:
```
http://127.0.0.1:8082/
```

> **Importante:** NO ejecutes `makemigrations` ni `migrate`. Las tablas ya existen en PostgreSQL. Django simplemente las usa.

---

## Endpoints

Todos los endpoints tienen el prefijo `/publicaciones/`.

| Método | Ruta | Descripción |
|---|---|---|
| `GET` | `/publicaciones/{recurso}/` | Listar todos los registros |
| `POST` | `/publicaciones/{recurso}/` | Crear un nuevo registro |
| `GET` | `/publicaciones/{recurso}/{id}/` | Obtener un registro por ID |
| `PUT` | `/publicaciones/{recurso}/{id}/` | Actualizar un registro completo |
| `PATCH` | `/publicaciones/{recurso}/{id}/` | Actualizar un registro parcialmente |
| `DELETE` | `/publicaciones/{recurso}/{id}/` | Eliminar un registro |

---

## Recursos disponibles

| Modelo | Ruta | Tabla en DB |
|---|---|---|
| Publicacion | `/publicaciones/publicacion/` | `publicacion` |
| ImagenPublicacion | `/publicaciones/imagenpublicacion/` | `imagenpublicacion` |
| SubCategoria | `/publicaciones/sub_categoria/` | `sub_categoria` |
| PublicacionCategoria | `/publicaciones/publicacioncategoria/` | `publicacioncategoria` |
| BienFisico | `/publicaciones/bienfisico/` | `bienfisico` |
| Servicio | `/publicaciones/servicio/` | `servicio` |
| BienDigital | `/publicaciones/biendigital/` | `biendigital` |
| Favorito | `/publicaciones/favorito/` | `favorito` |

---

## Modelos

### Publicacion
| Campo | Tipo | Descripción |
|---|---|---|
| id_publicacion | AutoField | PK |
| id_usuario | IntegerField | ID del usuario propietario |
| estadopublicacion | BooleanField | Estado de la publicación |
| titulo | CharField(150) | Título |
| descripcion | TextField | Descripción |
| tipo | CharField(20) | Tipo de publicación |
| visibilidad | CharField(20) | Visibilidad (publica/privada) |
| departamento | CharField(50) | Departamento |
| municipio | CharField(50) | Municipio |
| barrio | CharField(50) | Barrio opcional |
| disponible_para_trueque | BooleanField | Disponible para trueque |
| cantidad_disponible | IntegerField | Cantidad disponible |
| prioridad | IntegerField | Prioridad en listados |
| mensaje_contacto | TextField | Mensaje de contacto opcional |
| vistas | IntegerField | Número de vistas |
| favoritos | IntegerField | Número de favoritos |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### ImagenPublicacion
| Campo | Tipo | Descripción |
|---|---|---|
| id_imagen | AutoField | PK |
| id_publicacion | ForeignKey | Publicación asociada |
| url | TextField | URL de la imagen |
| tipo | CharField(20) | Tipo de imagen |
| orden | IntegerField | Orden de visualización |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### SubCategoria
| Campo | Tipo | Descripción |
|---|---|---|
| id_categoria | AutoField | PK |
| electronico | CharField(255) | Subcategoría electrónico |
| vehiculos | CharField(255) | Subcategoría vehículos |
| ropa | CharField(255) | Subcategoría ropa |
| libros | CharField(255) | Subcategoría libros |
| muebles | CharField(255) | Subcategoría muebles |
| juguetes | CharField(255) | Subcategoría juguetes |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### PublicacionCategoria
| Campo | Tipo | Descripción |
|---|---|---|
| id | AutoField | PK |
| id_publicacion | ForeignKey | Publicación asociada |
| id_categoria | ForeignKey | Subcategoría asociada |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### BienFisico
| Campo | Tipo | Descripción |
|---|---|---|
| id_bien | AutoField | PK |
| id_publicacion | OneToOneField | Publicación asociada |
| estado_producto | CharField(50) | Estado del producto |
| marca | CharField(100) | Marca |
| modelo | CharField(100) | Modelo |
| color | CharField(50) | Color |
| peso | DecimalField | Peso en kg |
| dimensiones | CharField(100) | Dimensiones |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### Servicio
| Campo | Tipo | Descripción |
|---|---|---|
| id_servicio | AutoField | PK |
| id_publicacion | OneToOneField | Publicación asociada |
| duracion | CharField(50) | Duración del servicio |
| modalidad | CharField(50) | Modalidad (presencial/virtual) |
| disponibilidad | TextField | Disponibilidad horaria |
| requisitos | TextField | Requisitos opcionales |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### BienDigital
| Campo | Tipo | Descripción |
|---|---|---|
| id_bien_digital | AutoField | PK |
| id_publicacion | OneToOneField | Publicación asociada |
| tipo_archivo | CharField(50) | Tipo de archivo |
| tamano_mb | DecimalField | Tamaño en MB |
| licencia | CharField(100) | Tipo de licencia |
| acceso_inmediato | BooleanField | Acceso inmediato tras trueque |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### Favorito
| Campo | Tipo | Descripción |
|---|---|---|
| id_favorito | AutoField | PK |
| id_usuario | IntegerField | ID del usuario |
| id_publicacion | ForeignKey | Publicación marcada como favorita |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

---

## Documentación Swagger

Disponible en:

```
http://127.0.0.1:8082/swagger/
http://127.0.0.1:8082/redoc/
```

---

## Base de datos

- **Motor:** PostgreSQL
- **Base de datos:** `xchango_db`
- **Schema:** `Publicaciones`

Las tablas fueron creadas previamente con el proyecto Go (Beego). Django se conecta directamente a ellas sin necesidad de migraciones.



# Xchango API — Módulo Sistema

API REST CRUD para el módulo de administración del sistema **Xchango**, desarrollada en **Django 6 + Django REST Framework + PostgreSQL**.

---

## Tecnologías

| Paquete | Versión |
|---|---|
| Python | 3.14 |
| Django | 6.0.5 |
| djangorestframework | 3.17.1 |
| drf-yasg | 1.21.15 |
| psycopg2-binary | 2.9.12 |
| python-decouple | 3.x |
| openpyxl | 3.x |

---

## Estructura del proyecto

xchango_django/
├── .env                    ← Variables de entorno (NO subir al repo)
├── .gitignore
├── manage.py
├── run.py                  ← Atajo para correr el servidor
├── backen/
│   ├── init.py
│   ├── settings.py         ← Configuración del proyecto
│   ├── urls.py             ← Rutas raíz + Swagger
│   ├── asgi.py
│   └── wsgi.py
└── api/
├── init.py
├── apps.py
├── models.py           ← 6 modelos del esquema 'sistema'
├── serializers.py      ← Serializadores de cada modelo
├── views.py            ← ViewSets CRUD + exportación Excel
├── urls.py             ← Enrutador con los 6 recursos
├── admin.py
├── tests.py
└── migrations/
└── init.py

---

## Instalación

```bash
# 1. Crear entorno virtual
python -m venv venv

# 2. Activar entorno virtual
venv\Scripts\activate.bat

# 3. Instalar dependencias
pip install django djangorestframework psycopg2-binary drf-yasg python-decouple setuptools openpyxl
```

---

## Variables de entorno (.env)

Crea un archivo `.env` en la raíz del proyecto con los siguientes valores:

```env
DB_NAME=*****
DB_USER=*****
DB_PASSWORD=*
DB_HOST=*****
DB_PORT=*****
DB_SCHEMA=***
```

---

## Correr el servidor

```bash
python run.py
```

El servidor inicia en:

http://127.0.0.1:8081/

> **Importante:** NO ejecutes `makemigrations` ni `migrate`. Las tablas ya existen en PostgreSQL. Django simplemente las usa.

---

## Endpoints

Todos los endpoints tienen el prefijo `/sistema/`.

| Método | Ruta | Descripción |
|---|---|---|
| `GET` | `/sistema/{recurso}/` | Listar todos los registros |
| `POST` | `/sistema/{recurso}/` | Crear un nuevo registro |
| `GET` | `/sistema/{recurso}/{id}/` | Obtener un registro por ID |
| `PUT` | `/sistema/{recurso}/{id}/` | Actualizar un registro completo |
| `PATCH` | `/sistema/{recurso}/{id}/` | Actualizar un registro parcialmente |
| `DELETE` | `/sistema/{recurso}/{id}/` | Eliminar un registro |
| `GET` | `/sistema/{recurso}/excel/` | Exportar todos los registros a Excel |

---

## Recursos disponibles

| Modelo | Ruta | Tabla en BD |
|---|---|---|
| Nivel de Acceso | `/sistema/nivel_acceso/` | `nivel_acceso` |
| Permiso | `/sistema/permiso/` | `permiso` |
| Administrador | `/sistema/administrador/` | `administrador` |
| Administrador Permiso | `/sistema/administradorpermiso/` | `administradorpermiso` |
| Historial Admin | `/sistema/historialadmin/` | `historialadmin` |
| Notificación | `/sistema/notificacion/` | `notificacion` |

---

## Exportación de datos a Excel

Cada recurso dispone de un endpoint dedicado para descargar todos sus registros en formato `.xlsx`.

### Endpoints `/excel/`

| Recurso | URL de exportación |
|---|---|
| Nivel de Acceso | `/sistema/nivel_acceso/excel/` |
| Permiso | `/sistema/permiso/excel/` |
| Administrador | `/sistema/administrador/excel/` |
| Administrador Permiso | `/sistema/administradorpermiso/excel/` |
| Historial Admin | `/sistema/historialadmin/excel/` |
| Notificación | `/sistema/notificacion/excel/` |

### Características de la exportación

- Generación automática de archivos `.xlsx`
- Descarga directa desde el navegador
- Exportación de todos los registros disponibles
- Compatible con Excel, LibreOffice y Google Sheets

### Ejemplo de uso

```bash
GET http://127.0.0.1:8081/sistema/notificacion/excel/
```

### Descarga del archivo

Al acceder al endpoint `/excel/`, el servidor responde con las cabeceras HTTP necesarias para forzar la descarga automática del archivo en el navegador:

Content-Type: application/vnd.openxmlformats-officedocument.spreadsheetml.sheet
Content-Disposition: attachment; filename="notificacion.xlsx"

---

## Modelos

### NivelAcceso
| Campo | Tipo | Descripción |
|---|---|---|
| id_nivelacceso | AutoField | Clave primaria |
| nombre | CharField(20) | Nombre del nivel |
| activo | BooleanField | Estado |
| fecha_asignacion | DateTimeField | Fecha de asignación |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### Permiso
| Campo | Tipo | Descripción |
|---|---|---|
| id_permiso | AutoField | Clave primaria |
| nombre | CharField(100) | Nombre del permiso |
| descripcion | TextField | Descripción opcional |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### Administrador
| Campo | Tipo | Descripción |
|---|---|---|
| id_admin | AutoField | Clave primaria |
| id_usuario | IntegerField | ID del usuario (FK externa) |
| id_nivelacceso | ForeignKey | Nivel de acceso asignado |
| activo | BooleanField | Estado |
| fecha_asignacion | DateTimeField | Fecha de asignación |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### AdministradorPermiso
| Campo | Tipo | Descripción |
|---|---|---|
| id | AutoField | Clave primaria |
| id_admin | ForeignKey | Administrador |
| id_permiso | ForeignKey | Permiso asignado |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### HistorialAdmin
| Campo | Tipo | Descripción |
|---|---|---|
| id_historial | AutoField | Clave primaria |
| id_admin | ForeignKey | Administrador que realizó la acción |
| accion | CharField(100) | Acción realizada |
| descripcion | TextField | Detalle opcional |
| tipo_objeto | CharField(50) | Tipo de objeto afectado |
| id_objeto | IntegerField | ID del objeto afectado |
| fecha_accion | DateTimeField | Fecha de la acción |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

### Notificacion
| Campo | Tipo | Descripción |
|---|---|---|
| id_notificacion | AutoField | Clave primaria |
| id_usuario | IntegerField | ID del usuario destino |
| titulo | CharField(100) | Título de la notificación |
| mensaje | TextField | Contenido del mensaje |
| tipo | CharField(50) | Tipo de notificación |
| id_referencia | IntegerField | ID del objeto relacionado |
| tipo_referencia | CharField(50) | Tipo del objeto relacionado |
| leido | BooleanField | Si fue leída |
| activo | BooleanField | Estado |
| fecha_creacion | DateTimeField | Fecha de creación |
| fecha_modificacion | DateTimeField | Última modificación |

---

## Documentación Swagger

Disponible en:
http://127.0.0.1:8081/swagger/
http://127.0.0.1:8081/redoc/

---

## Base de datos

- **Motor:** PostgreSQL
- **Base de datos:** `xchango_db`
- **Esquema:** `sistema`

Las tablas fueron creadas previamente con el proyecto Go (Beego). Django se conecta directamente a ellas sin necesidad de migraciones.
