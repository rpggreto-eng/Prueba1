# Panel · Controleventify

Panel de control con Firebase Firestore como base de datos.

## Credenciales de acceso
| Usuario | Contraseña |
|---------|-----------|
| gian    | 123       |
| greto   | 123       |

---

## Subir a GitHub Pages (3 pasos)

### 1. Crear repositorio en GitHub
- Ve a https://github.com/new
- Nombre: `panel` (o el que quieras)
- Selecciona **Public**
- Clic en **Create repository**

### 2. Subir el archivo
```bash
git init
git add index.html
git commit -m "Panel inicial"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/panel.git
git push -u origin main
```
O simplemente arrastra el `index.html` al repositorio desde la web de GitHub.

### 3. Activar GitHub Pages
- Ve a **Settings** → **Pages**
- Source: **Deploy from a branch**
- Branch: **main** → **/ (root)**
- Clic en **Save**

Tu panel estará en: `https://TU_USUARIO.github.io/panel`

---

## Configurar Firestore (IMPORTANTE)

Para que la base de datos funcione debes configurar las **reglas de Firestore**:

1. Ve a https://console.firebase.google.com
2. Selecciona el proyecto **controleventify**
3. Ve a **Firestore Database** → **Reglas**
4. Reemplaza las reglas con esto:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /{document=**} {
      allow read, write: if true;
    }
  }
}
```

5. Clic en **Publicar**

> ⚠️ Estas reglas permiten acceso abierto. Como el panel ya tiene login propio (gian/greto) esto es suficiente para uso interno.

---

## Colecciones en Firestore
El panel crea automáticamente estas colecciones al agregar datos:
- `users` — Jugadores/usuarios
- `warns` — Advertencias y sanciones
- `tickets` — Tickets de soporte
- `tasks` — Tareas internas
