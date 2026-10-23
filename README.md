# Backend Django: inventario y ventas

Proyecto académico de backend desarrollado con Python, Django y SQLite. Incluye dos aplicaciones: `productos` y `ventas`.

## Funcionalidades
- Listar y crear productos.
- Consultar, actualizar y eliminar un producto.
- Listar y crear ventas.
- Consultar y eliminar una venta.
- Al crear una venta, descuenta unidades del inventario; al eliminarla, las devuelve.
- Panel de administración de Django.

## Requisitos
- Python 3.10 o superior.
- Git.
- Cuenta de GitHub.

## Ejecutar en Windows
Abre una terminal dentro de esta carpeta y ejecuta:

```powershell
py -m venv venv
venv\Scripts\activate
py -m pip install -r requirements.txt
py manage.py makemigrations productos ventas
py manage.py migrate
py manage.py createsuperuser
py manage.py runserver
```

Abre `http://127.0.0.1:8000/`. El panel administrativo está en `http://127.0.0.1:8000/admin/`.

## Rutas API
- `GET /api/productos/` — lista de productos.
- `POST /api/productos/` — crea un producto.
- `GET /api/productos/1/` — consulta un producto por ID.
- `PUT /api/productos/1/` — actualiza un producto.
- `DELETE /api/productos/1/` — elimina un producto.
- `GET /api/ventas/` — lista ventas.
- `POST /api/ventas/` — crea una venta.
- `GET /api/ventas/1/` — consulta una venta por ID.
- `DELETE /api/ventas/1/` — elimina una venta y restaura el inventario.

Ejemplo JSON para crear producto:

```json
{
  "nombre": "Teclado",
  "descripcion": "Teclado USB",
  "precio": "45000.00",
  "cantidad": 10
}
```

Ejemplo JSON para crear venta (el producto debe existir):

```json
{
  "producto_id": 1,
  "cantidad": 2
}
```

Para probar POST/PUT/DELETE puedes usar una herramienta como Postman o Insomnia. Los endpoints están simplificados para una práctica local; antes de desplegar en producción se deben configurar autenticación, permisos, protección CSRF adecuada, variables de entorno y `DEBUG = False`.

## Subir a GitHub
1. Crea un repositorio vacío en GitHub, por ejemplo `backend-django-inventario`.
2. No marques README, `.gitignore` ni licencia al crearlo, porque ya están en esta carpeta.
3. En una terminal abierta en esta carpeta ejecuta:

```bash
git init
git add .
git commit -m "Backend Django inicial"
git branch -M main
git remote add origin https://github.com/TU-USUARIO/backend-django-inventario.git
git push -u origin main
```

Cambia `TU-USUARIO` por tu nombre real de usuario de GitHub. Inicia sesión cuando el navegador te lo solicite. Luego copia la URL de tu repositorio y entrégala en EVA.

## Importante
No subas contraseñas reales, tokens ni archivos `.env`. La base de datos local `db.sqlite3` y el entorno virtual `venv/` están excluidos por `.gitignore`.
