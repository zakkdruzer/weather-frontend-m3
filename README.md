# Weather Chile - Módulo 3 · App de Clima

Proyecto de final de módulo desarrollado como parte del **Módulo 3** del curso de Frontend. Refactoriza la app de clima del módulo anterior, enfocándose en **interfaz**, **organización de estilos**, **SASS** y **layout responsive**.

## Descripción

Weather Chile es una aplicación frontend construida con **HTML5 semántico**, **Bootstrap 5**, **SASS/CSS3** y **JavaScript**.

La app permite:

- Visualizar una grilla de localidades en la vista principal (Home).
- Consultar el clima actual de cada ciudad.
- Mostrar el detalle de la localidad seleccionada dentro de la misma página.
- Revisar temperatura, humedad, viento y pronóstico semanal.

## Funcionalidades principales

- Home con 10 localidades de Chile.
- Cards Bootstrap con:
  - nombre de la ciudad,
  - región,
  - icono del clima,
  - temperatura,
  - estado actual.
- Vista de detalle con:
  - resumen de la ciudad seleccionada,
  - métricas principales (temperatura, humedad, viento),
  - pronóstico semanal de 7 días.
- Navegación controlada con JavaScript sin recargar la página.
- Scroll suave entre secciones (home ↔ detalle).
- Diseño responsive para móvil y escritorio.

## Metodología de estilos

Para la organización de estilos se utiliza la metodología **BEM (Block, Element, Modifier)**, aplicada sobre la capa de estilos personalizada.[file:1]

Ejemplos de bloques y elementos:

- Bloque raíz de la app: `weather-app`.
- Bloques de interfaz:
  - `weather-app__home` para la sección de localidades.
  - `weather-app__detail` para la vista de detalle.
- Bloque de card de ciudad:
  - `place-card` (bloque),
  - `place-card__title`, `place-card__region`, `place-card__temp`, `place-card__status`, `place-card__button` (elementos),
  - modificadores pensados para estados de clima (`place-card--hot`, `place-card--cold`, etc.).

BEM convive con las clases de Bootstrap, que se usan para layout y utilidades (grid, spacing, tipografía).

## SASS y estructura de estilos

Los estilos se modularizan usando **SASS** con parciales, variables, anidamiento y al menos un mixin reutilizable.[file:1]

Estructura principal de SASS:

```bash
scss/
├── base/
│   ├── _variables.scss   # Colores, tipografías, tamaños, breakpoints
│   └── _mixins.scss      # Mixins reutilizables (ej. tarjetas elevadas)
├── layout/
│   └── _layout.scss      # Body, main, hero, footer, reglas globales y media queries
├── components/
│   ├── _place-card.scss  # Estilos del bloque .place-card y sus elementos BEM
│   └── _detail.scss      # Estilos de la vista de detalle y .detail-hero
└── main.scss             # Importa todos los parciales y genera el CSS final
```

En `main.scss` se importan los parciales y se compila a `css/styles.css`, que es el archivo enlazado en `index.html`.[file:1]

Características de SASS utilizadas:

- **Variables** para colores de fondo, gradientes y breakpoints.
- **Anidamiento** para agrupar estilos de un mismo bloque (por ejemplo, `.place-card` y sus elementos).
- **Mixin** para reutilizar estilos de tarjetas elevadas en distintos componentes (cards de ciudades y hero de detalle).
- **Parciales** separados por responsabilidad (base, layout, componentes).
- El mixin de tarjetas elevadas se aplica tanto a las cards de ciudades como al bloque principal de detalle, asegurando una apariencia consistente sin duplicar código.

## Layout y responsividad

El layout combina **HTML semántico** con el **grid de Bootstrap**:[file:1]

- Estructura principal con `header`, `nav`, `main`, `section`, `article` y `footer`.
- Navbar responsive con Bootstrap (colapsable en pantallas pequeñas).
- Grilla de cards de ciudades usando el sistema de columnas:
  - `col-12` en pantallas pequeñas (1 columna),
  - `col-sm-6` en pantallas medianas (2 columnas),
  - `col-lg-4` en pantallas grandes (3 columnas).
- Sección de detalle con un bloque destacado (`detail-hero`) que utiliza un gradiente y tarjetas para las métricas.

En conjunto, esto cumple el requisito de que en pantallas pequeñas las cards se muestran apiladas y en pantallas grandes se distribuyen en varias columnas.[file:1]

## Tecnologías utilizadas

- HTML5
- SASS/CSS3
- Bootstrap 5
- JavaScript (DOM y eventos)

## Estructura del proyecto

```bash
weather-frontend-m3/
├── index.html
├── README.md
├── css/
│   └── styles.css        # CSS compilado desde SASS
├── scss/
│   ├── base/
│   │   ├──_mixins.scss
│   │   └──_variables.scss
│   ├── layout/
│   │   └──_layout.scss
│   ├── components/
│   │   ├──_detail.scss
│   │   └──_place-card.scss
│   └── main.scss
└── js/
    ├── data.js           # Datos de clima por ciudad
    └── main.js           # Lógica de render, navegación y detalle
```

## Cómo ejecutar el proyecto

1. Clona o descarga este repositorio.
2. Abre el archivo `index.html` en tu navegador.
3. En la vista Home, haz clic en una ciudad para ver su detalle y pronóstico semanal.
4. Usa la navegación superior o el botón “Volver al inicio” para regresar a la grilla de localidades.

> Opcional para desarrollo: puedes ejecutar `sass scss/main.scss css/styles.css --watch` para recompilar los estilos mientras editas.

## Control de versiones

Se trabajó con **commits descriptivos** para reflejar el progreso del módulo, por ejemplo:

- `primer commit`
- `estructura base SASS`
- `compilacion SASS lista`
- `toques finales de SASS listos`
- `actualizar README para módulo 3`
- `ultimos cambios de README`

## Repositorio

`https://zakkdruzer.github.io/weather-frontend-m3/`

## Estado del proyecto

- MVP funcional completado para Módulo 3.
- Listo para futura integración con API de clima en módulos siguientes.