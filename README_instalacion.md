# OPE Osakidetza Test

## Qué incluye
- Todo aleatorio
- Temario Específico por bloques de 50
- Común C2, C3, D y E por bloques de 50
- Shuffle de respuestas
- Apartado de falladas con repaso
- Guardado local automático
- Sincronización opcional con Supabase
- PWA instalable en PC y Android

## Archivos importantes
- `index.html`: app principal
- `questions-data.js`: banco de preguntas completo
- `app-config.js`: aquí pones la URL y la anon key de Supabase
- `supabase_schema.sql`: SQL para crear la tabla de sincronización
- `manifest.webmanifest` + `sw.js`: para instalarla como app

## Lo mínimo para usarla ya en tu PC
1. Descomprime la carpeta.
2. Abre una terminal dentro de esta carpeta.
3. Lanza un servidor local.
   - Si tienes Python: `python -m http.server 8080`
4. Abre `http://localhost:8080`

## Para tenerla en PC y Android con sincronización
### 1) Crear Supabase
1. Crea un proyecto en Supabase.
2. Ve a SQL Editor.
3. Ejecuta el contenido de `supabase_schema.sql`.
4. Ve a Authentication y activa Email/Password.
5. Copia:
   - Project URL
   - anon public key

### 2) Configurar la app
1. Abre `app-config.js`
2. Sustituye:
```js
window.APP_CONFIG = {
  SUPABASE_URL: 'https://TU-PROYECTO.supabase.co',
  SUPABASE_ANON_KEY: 'TU_ANON_KEY'
};
```

### 3) Publicarla
Puedes subir esta carpeta a cualquier hosting estático con HTTPS.
Opciones sencillas:
- GitHub Pages
- Netlify
- Vercel

### 4) Instalarla
- En PC: abre la web en Chrome o Edge y usa el botón **Instalar app**.
- En Android: abre la web en Chrome y usa **Añadir a pantalla de inicio** o **Instalar app**.

## Cómo funciona la sync
- Sin cuenta: guardado local en ese dispositivo.
- Con cuenta: el progreso se guarda además en Supabase.
- Usa el mismo email en PC y Android.
- Pulsa **Sincronizar ahora** si quieres forzar el guardado inmediato.

## Notas
- La sync guarda el estado completo de progreso, falladas, sesiones y ajustes.
- La app sigue funcionando offline una vez cargada.
- Si cambias preguntas o estructura, conviene aumentar la versión del cache en `sw.js`.
