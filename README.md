# Formulador MML SENA
### Herramienta interactiva de formulación de proyectos con Metodología de Marco Lógico

**Jóvenes en Ciencia para la Paz – Capítulo Ipiales**  
Suroccidente nariñense · SENA · MinCiencias

🌐 **App en vivo:** [roserocarlos.github.io/SENAformuladorMML](https://roserocarlos.github.io/SENAformuladorMML)

---

## ¿Para qué sirve?

Esta herramienta guía a equipos de jóvenes innovadores en la **formulación y ejecución de proyectos CTel** (Ciencia, Tecnología e Innovación) usando la Metodología de Marco Lógico (MML), alineada con los formatos SENNOVA, MGA y las guías de marco lógico de MinCiencias.

Está diseñada para jóvenes que **ya ganaron una convocatoria de innovación** y necesitan formular correctamente su proyecto para ejecutar los recursos asignados. También sirve para futuras convocatorias.

---

## Funcionalidades principales

### 10 sesiones de formulación guiadas
Cada sesión avanza una o varias secciones de la plantilla MML:

| Sesión | Contenido | Secciones |
|--------|-----------|-----------|
| 1 | Líneas temáticas y enfoque CTel | S1 Identificación · S2 Resumen |
| 2 | Formulación del problema central | S3 Árbol de problemas |
| 3 | Causas y efectos (árbol jerárquico) | S3 completo |
| 4 | Árbol de objetivos | S4 completo |
| 5 | Objetivo específico y resultados | S5 Objetivos |
| 6 | Objetivo general, actividades y cadena lógica | S5 · S7 Actividades |
| 7 | Indicadores IOV | S6 Matriz MML · S9 Productos |
| 8 | Medios de verificación y supuestos | S6 Matriz MML completa |
| 9 | Presupuesto SENA y gestión de riesgos | S8 · S10 |
| 10 | Sostenibilidad e impactos | S11 · S12 |

### Árbol de problemas y objetivos — visual jerárquico
Cajas y conectores por niveles (efectos 2.° orden → efectos directos → problema central → causas directas → causas 2.° orden), editable en línea. La misma estructura espeja el árbol de objetivos.

### Actividades dinámicas asociadas a resultados
Se genera exactamente un bloque de actividades por cada resultado esperado definido. Cada actividad tiene código automático `A1.1`, `A1.2`… y validación de sustantivos de acción (construcción, capacitación, diseño, implementación…).

### Cadena de coherencia lógica
Panel visual que valida eslabón por eslabón:  
`Actividades → Resultados → Objetivo específico → Objetivo general`

### Indicadores IOV dinámicos
Un bloque de indicador por cada resultado esperado (Redacción · Línea de base · Meta · Plazo). Los campos aparecen automáticamente según los resultados definidos en la Sesión 5.

### Presupuesto por rubros SENA
7 rubros elegibles según la convocatoria:
- Recurso humano
- Materiales e insumos
- Consultorías y asesorías especializadas
- Maquinaria y equipos
- TIC — Tecnologías de información y comunicaciones
- Transferencia de tecnología
- Servicios externos

Cada ítem se asocia directamente a una actividad del proyecto (`A1.1`, `A2.3`…) y requiere justificación técnica. Total general calculado automáticamente.

### Mapa de riesgos Probabilidad × Impacto
Matriz de calor 3×3 con ubicación automática de riesgos. Tipos: Técnico · Financiero · Administrativo · Externo · Legal. Cada riesgo incluye estrategia de mitigación y plan de contingencia.

### Exportar PDF
Genera el documento completo del proyecto (portada, árbol de problemas, árbol de objetivos, MML, presupuesto) listo para entregar como Anexo 2.

---

## Guardado de datos — 3 capas de protección

Para 80 usuarios con meses de trabajo formulando, la herramienta implementa tres capas simultáneas:

```
Capa 1 — localStorage     → guarda en cada tecla, sin internet
Capa 2 — Google Drive     → guarda automáticamente cada 2 segundos
Capa 3 — Respaldo JSON    → descarga manual del formulario completo
```

- Si el usuario cierra el navegador sin querer → **localStorage** tiene todo
- Si cambia de computador → **Drive** tiene todo
- Si quiere copia de seguridad propia → **Exportar respaldo .json** en el sidebar
- El token OAuth se renueva automáticamente cada 50 minutos

---

## Tecnologías

- **HTML + CSS + JavaScript vanilla** — un solo archivo, sin dependencias de build
- **Google Identity Services** — autenticación OAuth 2.0
- **Google Drive API v3** — guardado en `appDataFolder` (privado por usuario)
- **jsPDF + html2canvas** — exportación a PDF en el navegador
- **GitHub Pages** — hosting estático gratuito

---

## Estructura del repositorio

```
SENAformuladorMML/
├── index.html        # Aplicación completa (un solo archivo)
└── README.md         # Este archivo
```

---

## Despliegue

### Requisitos
- Cuenta en GitHub
- Proyecto en Google Cloud con Drive API habilitada
- Client ID de OAuth 2.0 configurado para `https://roserocarlos.github.io`

### Configuración del Client ID

En `index.html`, línea ~160:

```javascript
const GOOGLE_CLIENT_ID = '833147808780-uijlecklphgdca5ebdjih0lvrgeenc0i.apps.googleusercontent.com';
```

### Google Cloud — pasos realizados
- [x] Proyecto `SENAformuladorMML` creado
- [x] Google Drive API habilitada
- [x] Pantalla de consentimiento OAuth configurada (Externa)
- [x] Client ID creado para origen `https://roserocarlos.github.io`

### GitHub Pages
Settings → Pages → Branch: `main` → `/(root)` → Save

URL resultante: `https://roserocarlos.github.io/SENAformuladorMML`

---

## Datos que guarda en Drive

La app usa el `appDataFolder` de Google Drive — una carpeta especial **invisible para el usuario** en su Drive personal que solo esta app puede leer. No tiene acceso a ningún otro archivo del Drive del usuario.

Archivo guardado: `formuladorMML_datos.json`  
Contiene: todos los campos del formulario, sesiones completadas, sesión activa.

**El administrador de la app no tiene acceso a los datos de los usuarios.**

---

## Privacidad

- Cada usuario autoriza acceso únicamente a sus propios datos
- Los datos se guardan en el Drive personal de cada usuario
- El desarrollador no almacena ni procesa datos de los formuladores
- Scope utilizado: `https://www.googleapis.com/auth/drive.appdata`

---

## Municipios del suroccidente nariñense cubiertos

Aldana · Contadero · Córdoba · Cuaspud · Cumbal · Funes · Guachucal · Guaitarilla · Gualmatán · Iles · Imués · Ipiales · Ospina · Potosí · Puerres · Pupiales · Ricaurte · Sapuyes · Túquerres

---

## Créditos

Desarrollado para el programa **Jóvenes en Ciencia para la Paz – Capítulo Ipiales**  
Convocatoria SENA · Cámara de Comercio de Ipiales · MinCiencias  

Herramienta diseñada con base en:
- Metodología General Ajustada (MGA) — DNP Colombia
- Formatos SENNOVA — SENA
- Guías de Marco Lógico — CIDEAL, Acción contra el Hambre, CPC Oriente
- Términos de referencia Convocatoria "Jóvenes en Ciencia para la Paz"

---

## Licencia

Uso libre para fines educativos y de formulación de proyectos de innovación social y CTel en Colombia.
