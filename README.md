# 🎓 AsistenciaApp

Sistema de control de asistencia escolar para nivel secundaria.  
Sin instalación, sin internet, funciona directo en el navegador.

---

## Archivos

```
asistencia.html   →   toma de asistencia diaria
reportes.html     →   estadísticas y gráficas globales
```

Ábrelos directo en Chrome, Firefox o Edge. No necesitan servidor.

---

## Flujo de uso

```
1. Abre asistencia.html
2. Elige el grado (1°, 2° o 3°)
3. Marca a cada alumno: ✅ Presente  o  ❌ Falta
4. Guarda el JSON del día
5. Cuando quieras ver el resumen, abre reportes.html
   y arrastra todos los JSON que hayas guardado
```

---

## Agregar o quitar alumnos

Abre `asistencia.html` y edita el objeto `ALUMNOS` al inicio del script:

```js
const ALUMNOS = {
  1: [                              // 1° Primero
    { id: 1, nombre: "Nombre Completo" },
    { id: 2, nombre: "Otro Alumno"     },
  ],
  2: [ ... ],                       // 2° Segundo
  3: [ ... ],                       // 3° Tercero
};
```

Solo respeta el formato `{ id, nombre }` y que los ids sean consecutivos.

---

## JSON que genera la app

Cada vez que guardas, se descarga un archivo como:  
`asistencia_1grado_2025-05-29.json`

```json
{
  "grado": 1,
  "gradoNombre": "Primero",
  "fecha": "2025-05-29",
  "alumnos": [
    { "id": 1, "nombre": "pepito", "asistio": true  },
    { "id": 2, "nombre": "nombre generico 2*",     "asistio": false },
    { "id": 3, "nombre": "juanito",   "asistio": null  }
  ]
}
```

| Valor | Significado     |
|-------|-----------------|
| true  | Presente        |
| false | Falta           |
| null  | Sin registrar   |

---

## Reportes

Carga uno o varios JSON en `reportes.html` y obtienes:

- Totales globales (alumnos, asistencias, faltas, %)
- Gráfica de dona — distribución general
- Gráfica de barras — comparativo entre grados
- Tabla por alumno con barra de % de asistencia
- Filtros por grado

Puedes mezclar archivos de distintos días; la app los acumula automáticamente.

---

## Exportar PDF

En `asistencia.html`, después de capturar la asistencia del día,  
presiona **📄 Exportar PDF** — se descarga listo para imprimir.
