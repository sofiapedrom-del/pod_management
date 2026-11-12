# Cash Flow Pod Tracker

Dashboard de clientes, responsables y status del Cash Flow Pod, publicado en GitHub Pages. Son dos archivos en la raíz del repositorio: `index.html` (la página) y `data.json` (los datos).

## Usar el dashboard

**Board:** una columna por etapa. Arrastrá una tarjeta a otra columna para cambiar la etapa, o soltala sobre otra tarjeta para cambiar el orden. Cada cambio de etapa queda registrado solo en las notas del cliente.

**List:** tabla con un selector de etapa en cada fila, útil desde el celular.

**Editar un cliente:** click en la tarjeta o en la fila. Se puede cambiar el nombre, la etapa, el responsable, el status, la próxima acción con su fecha y agregar o borrar notas. **+ Add client** suma un cliente nuevo.

**Print / PDF:** abre la ventana de impresión con un reporte armado por etapa. En destino elegí "Save as PDF". El archivo sale con el nombre `Cash Flow Pod Status AAAA-MM-DD`.

## Guardar los cambios

Mientras no guardes, los cambios viven solo en tu navegador y aparece un aviso amarillo arriba. Hay dos formas de publicarlos.

### Opción A, botón Save changes (recomendada)

Se configura una sola vez:

1. En GitHub, tu foto, **Settings, Developer settings, Personal access tokens, Fine grained tokens, Generate new token**.
2. Nombre: `Cash Flow Pod Tracker`. Expiración: la que prefieras.
3. Repository access: **Only select repositories** y elegí el repositorio del tracker.
4. Permissions, Repository permissions, **Contents: Read and write**. Generate token y copialo.
5. En el dashboard, **Settings**: owner y repositorio se completan solos, pegá el token y **Save settings**.

Desde ahí, **Save changes** guarda directo en `data.json` del repositorio y el link público se actualiza en un minuto aproximadamente. El token queda guardado solo en tu navegador; cada persona que quiera editar necesita su propio token. Si lo perdés o cambiás de computadora, generás uno nuevo.

### Opción B, sin token

En el aviso amarillo, **Download data.json**. Después, en el repositorio, **Add file, Upload files**, subí ese archivo para reemplazar el anterior y Commit.

## Campos de data.json

| Campo | Qué es |
|---|---|
| `team` | Miembros del equipo que aparecen como responsables |
| `stages` | Etapas del board, en orden |
| `owner` | Responsable del cliente. Vacío muestra "Unassigned" |
| `stage` | Etapa actual, una de `stages` |
| `status` | Frase corta debajo del nombre |
| `nextAction`, `nextDate` | Próxima acción y su fecha (`AAAA-MM-DD`). Rojo si está vencida, amarillo si es hoy |
| `notes` | Historial con fecha y texto |

Para sumar alguien al equipo o cambiar las etapas, editá `team` o `stages` en `data.json` desde GitHub.

Si la página muestra "Could not read data.json", casi siempre es una coma de más o de menos en el JSON. Se puede validar en jsonlint.com.
