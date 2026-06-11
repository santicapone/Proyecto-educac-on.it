# Proyecto Integrador — E-commerce
## Primera Entrega: HTML, CSS y estructura base

| Fecha de entrega: Miércoles 10 de Junio, 2026 |
|-----------------------------|

Este proyecto es el trabajo final del curso. A lo largo de tres entregas vas a construir un e-commerce completo: desde la maqueta estática hasta una aplicación React conectada a tu propio backend con base de datos real.

En esta primera etapa el foco está en la **estructura visual**: HTML semántico, CSS organizado y diseño responsive. No hay JavaScript ni datos dinámicos — todo es estático. Pero las decisiones que tomés acá van a afectar directamente las entregas siguientes: si los nombres de productos no son coherentes entre páginas, o si el HTML no tiene estructura semántica, vas a tener que rehacer trabajo más adelante.

> 💡 "Responsive" no significa que se vea "más o menos bien" en mobile. Significa que la experiencia fue pensada y diseñada para cada tamaño de pantalla. Antes de escribir CSS, abrí el sitio de referencia que elegiste en mobile y en desktop, y notá qué cambia: qué se oculta, qué se reorganiza, qué sigue igual.

---

## Diseño de referencia

No hay un diseño obligatorio a seguir — el diseño es tuyo. Lo que sí es obligatorio es que el resultado sea **cuidado, coherente y atractivo**. Un e-commerce mal diseñado no convence a nadie de comprar.

Antes de escribir una línea de código, buscá inspiración. Mirá cómo otros resolvieron los mismos problemas: cómo organizaron el navbar, cómo presentaron las cards de producto, qué jerarquía visual usaron. Después tomá decisiones propias.

**Dónde buscar inspiración:**

| Recurso | Para qué sirve |
|---------|---------------|
| [ThemeForest](https://themeforest.net/category/site-templates/ecommerce) | Templates de e-commerce completos — excelente referencia de layouts y jerarquía visual |
| [TemplateMonster](https://www.templatemonster.com/ecommerce-templates/) | Otra colección de templates con diseños variados y modernos |
| [Dribbble](https://dribbble.com/search/ecommerce) | Diseños de UI de alta calidad — útil para cards, navbars y secciones hero |
| [Behance](https://www.behance.net/search/projects/ecommerce%20ui) | Proyectos completos de diseño con proceso y detalle |
| [Awwwards](https://www.awwwards.com) | Los sitios más reconocidos del mundo por diseño y UX — para ver el nivel de excelencia |

> 💡 Mirar templates no es copiar — es aprender. Los diseñadores profesionales estudian lo que ya existe antes de crear algo nuevo. Lo que hacés con esa información es lo que te diferencia.

---

## Convenciones generales

Estas reglas aplican a las tres entregas. Empezar con ellas incorporadas te ahorra correcciones en el futuro:

- **Indentación consistente**: 2 espacios. Sin mezclar tabs y espacios.
- **Sin código comentado**: si algo no va, borralo. El archivo limpio es más fácil de leer y corregir.
- **Clases descriptivas**: `.product-card` dice más que `.card1`. `.nav-links` dice más que `.div2`. El nombre tiene que describir qué es el elemento, no dónde está o cómo se ve.

---

## Buenas prácticas de CSS

### Variables CSS

Es opcional pero podría ayudarte mucho tener todas las decisiones de diseño como variables en `:root` al inicio de `styles.css`. Colores, tipografías, espaciados y bordes — todo en un solo lugar. Si el día de mañana el cliente te pide cambiar el color primario, lo cambiás en una línea y se actualiza en todo el sitio. Ejemplo, no es una definición obligatoria, es solo una referencia:

```css
:root {
  /* Colores */
  --color-primary:    #2563eb;
  --color-secondary:  #1e40af;
  --color-accent:     #f59e0b;
  --color-text:       #1f2937;
  --color-text-light: #6b7280;
  --color-bg:         #ffffff;
  --color-bg-alt:     #f9fafb;
  --color-border:     #e5e7eb;

  /* Tipografía */
  --font-primary: 'Inter', sans-serif;
  --font-size-sm:   0.875rem;  /* 14px */
  --font-size-base: 1rem;      /* 16px */
  --font-size-lg:   1.125rem;  /* 18px */
  --font-size-xl:   1.25rem;   /* 20px */
  --font-size-2xl:  1.5rem;    /* 24px */
  --font-size-3xl:  1.875rem;  /* 30px */

  /* Espaciado */
  --spacing-sm:  0.5rem;    /*  8px */
  --spacing-md:  1rem;      /* 16px */
  --spacing-lg:  1.5rem;    /* 24px */
  --spacing-xl:  2rem;      /* 32px */
  

  /* Bordes */
  --radius-sm: 4px;
  --radius-md: 8px;
  --radius-lg: 16px;

  /* Sombras */
  --shadow-sm: 0 1px 3px rgba(0, 0, 0, 0.1);
  --shadow-md: 0 4px 6px rgba(0, 0, 0, 0.1);
  --shadow-lg: 0 10px 15px rgba(0, 0, 0, 0.1);

  /* Transiciones */
  --transition: 0.2s ease;
}
```

Usálas así en el resto de tus archivos CSS:

```css
.btn-primary {
  background-color: var(--color-primary);
  color: var(--color-bg);
  padding: var(--spacing-sm) var(--spacing-lg);
  border-radius: var(--radius-md);
  transition: background-color var(--transition);
}

.btn-primary:hover {
  background-color: var(--color-secondary);
}
```

> 💡 es conveniente que no escribas un color, tamaño o espaciado "a mano" en el CSS de un componente. Si escribís `color: #2563eb` en diez lugares distintos y después querés cambiarlo, tenés que buscarlo en diez lugares. Con variables, lo cambiás en `:root` y listo.

---

### Media queries

Puedes usar un enfoque **mobile-first**: escribiendo los estilos base pensando en mobile y sobreescribí con media queries para pantallas más grandes. Es más fácil agregar complejidad visual en pantallas grandes que quitarla en pantallas chicas.

Definí los breakpoints como variables y usálos de forma consistente en todo el proyecto:

```css
/* Breakpoints de referencia */
/* sm:  640px  — teléfonos grandes en horizontal */
/* md:  768px  — tablets                         */
/* lg:  1024px — laptops                         */
/* xl:  1280px — desktops                        */

/* Ejemplo mobile-first */
.products-grid {
  display: flex;
  flex-direction: column;   /* mobile: elementos apilados */
  gap: 16px;
}

@media (width > 768px) {
  .products-grid {
    flex-direction: row;
    flex-wrap: wrap;
  }
}

```

> 💡 Usá siempre los mismos breakpoints en todo el proyecto. Si en el navbar rompés el layout en `768px`, rompelo también en las cards y en el footer. La inconsistencia en los breakpoints es una de las causas más comunes de layouts "raros" en ciertos tamaños de pantalla.

---

### Armonía visual del sitio

Un buen diseño no es solo que cada página se vea bien por separado — es que todas las páginas se vean como parte de un mismo sistema. Algunos puntos clave:

**Paleta de colores limitada:** definí 2 colores principales (primario y secundario), 1 color de acento para llamadas a la acción, y neutros para texto y fondos. Más de eso y el diseño se ve sobrecargado.

**Tipografía consistente:** usá máximo 2 fuentes en todo el sitio — una para títulos y una para texto corriente (o incluso una sola). Definí una escala tipográfica y no la rompas: los `h1` siempre del mismo tamaño, los `h2` siempre del mismo, los párrafos siempre con el mismo `line-height`.

**Espaciado sistemático:** usá los valores de `--spacing-*` definidos en `:root`. Evitá valores arbitrarios como `margin: 13px` o `padding: 27px` — generan inconsistencias visuales difíciles de detectar.

**Componentes reutilizables:** el navbar, el footer, las cards y los botones se repiten en múltiples páginas. Definí sus estilos una sola vez y reutilizalos. Si el botón primario se ve diferente en el Home y en el Register, algo está mal.

**Jerarquía visual clara:** en cada página tiene que quedar claro qué es lo más importante. Usá tamaño, peso tipográfico y color para guiar la mirada del usuario. Un `h1` que tiene el mismo peso visual que el resto del texto no funciona como título.

> 💡 Antes de escribir CSS, abrí los templates que tomaste como referencia y analizalos: ¿cuántos colores usan? ¿Cómo manejan el espaciado entre secciones? ¿Cómo diferencian títulos de subtítulos? Esas decisiones no son casuales — son el resultado de principios de diseño que podés aprender mirando con atención.

---

## Estructura del proyecto

```
ecommerce/
├── index.html              ← Página principal (Home) — queda en la raíz
├── pages/
│   ├── register.html
│   ├── contact.html
│   ├── products.html
│   ├── product-detail.html
│   ├── admin-products.html
│   └── about.html
├── css/
│   ├── styles.css          ← Estilos globales (variables, reset, tipografía)
│   ├── home.css            ← Estilos específicos del Home
│   ├── register.css        ← Estilos específicos del Register
│   ├── product-detail.css
│   ├── admin.css
│   └── about.css
└── assets/
    └── videos/
    └── images/
        ├── logo.png
        └── products/
            ├── product-1.jpg
            └── ...
```

> 💡 `index.html` queda en la raíz porque es el punto de entrada del sitio — los servidores web lo buscan ahí por convención. El resto de las páginas van dentro de `pages/` para mantener la raíz limpia. Al hacer links entre páginas, acordate de ajustar las rutas: desde `index.html` un link al register sería `href="pages/register.html"`, y desde cualquier página dentro de `pages/` un link al home sería `href="../index.html"`.

---

## Componentes compartidos

### Header y Navbar

El navbar debe:

- Estar **fijo en la parte superior** (`position: sticky o fixed`) — al hacer scroll, se mantiene visible
- En **mobile**: los links se ocultan por defecto y se despliegan al hacer clic en el ícono de hamburguesa
- En **desktop**: todos los links visibles en una sola línea

**Links requeridos:**
- Principal → `index.html`
- Productos → `pages/products.html`
- Registro → `pages/register.html`
- Contacto → `pages/contact.html`
- Acerca de → `pages/about.html`
- Admin Productos → `pages/admin-products.html`

**Zona de usuario (derecha del navbar):**
- Avatar del usuario (puede ser una imagen de placeholder)
- Ícono del carrito de compras
- Botón de login/logout (sin funcionalidad en esta entrega)

> 💡 El menú hamburguesa: al hacer clic en el ícono, agregás o removés una clase CSS al contenedor de links (por ejemplo `.nav-links.open`). En CSS definís que por defecto en mobile `.nav-links` está oculto (`display: none`) y que `.nav-links.open` está visible. Solo necesitás un `addEventListener('click', ...)` en el botón.

---

### Footer

El contenido del footer debe tener estos elementos mínimos: El orden como se disponen puede quedar a tu criterio pero debe verse bien tanto en mobile como desktop, lo importante es que estén presentes y que el diseño sea cuidado. El footer es la última impresión que el usuario tiene de tu sitio — no lo descuides.

El footer debe tener **tres columnas**:

| Columna | Contenido sugerido |
|---------|--------------------|
| 1 | Logo del sitio + nombre |
| 2 | Redes sociales (íconos con links) colocar enlace: LinkedIn, Facebook, Twitter |
| 3 | Información de contacto (email, teléfono, dirección) |

El orden de las columnas es libre. Comportamiento responsive:
- **Mobile**: una columna (secciones apiladas verticalmente)
- **Tablet / Desktop**: tres columnas en una misma fila, esto puede ser opcional ya que podríamos colocar 2 elementos uno al lado del otro y el tercero debajo, esto depende del diseño que elijan.


---

## Páginas

### Home (index.html)

La página principal tiene cuatro secciones en este orden:

#### 1. Banner

Un banner que ocupe el **ancho completo** de la pantalla. Puede ser:
- Una imagen fija de fondo o un video (puede ser un loop de un producto en acción, por ejemplo)
- Un hero div con un texto grande y llamativo puede estar acompañado de párrafos, botones de llamada a la acción o cualquier otro elemento que consideres relevante para presentar el negocio.
- Un carrusel animado (opcional)

#### 2. Hero Section

Dividida en dos columnas:
- **Izquierda**: título y texto de introducción al ecommerce
- **Derecha**: imagen representativa del negocio o un carousel de imágenes (opcional)

En mobile, las dos columnas se apilan (una encima de la otra) pueden cambiar el orden según consideren necesario.

#### 3. Productos destacados

Un grillado de **al menos 8 productos** en formato card. Cada card debe mostrar:

| Campo | Obligatorio |
|-------|-------------|
| Imagen del producto | ✅ |
| Nombre del producto | ✅ |
| Categoría | ✅ |
| Precio | ✅ |
| Botón "Comprar" | ✅ |
| Botón "Ver más" | ✅ No tiene por que decir ver más puede ser cualquier texto que indique más información o icono pero debe estar presente y permitir al usuario acceder a más detalles |
| Descripción | Opcional |
| Fecha de ingreso | Opcional |

El grillado debe ser responsive. Referencia orientativa:
- Mobile: 1 columna
- Pantallas más grandes los elementos que quepan en una fila se acomodan automáticamente (puede ser 2, 3 o 4 columnas dependiendo del ancho disponible)

> 💡 Con `display: flex` y `flex-wrap: wrap` en el contenedor, y `flex: 1 1 250px` en cada card, los elementos se acomodan solos según el ancho disponible: en mobile quedan apilados, en pantallas más grandes se distribuyen en filas. Es simple y predecible.

> 💡 Los datos de los 8 productos tienen que ser **coherentes** entre páginas. Si en el Home el producto 1 se llama "Teclado mecánico RGB" y cuesta $85.000, en el Admin y en el Detalle tiene que aparecer el mismo nombre y precio. Esto parece obvio pero es uno de los errores más comunes.

#### 4. Características del servicio

Una sección debajo del grillado de productos con las **ventajas o características** del negocio con al menos 3 elementos (por ejemplo: "Envío gratis", "Garantía 12 meses", "Soporte 24/7").

- **Mobile**: cada característica apilada verticalmente (una columna)
- **Desktop**: todas en fila (una sola fila)

Cada característica debe tener al menos un ícono y un texto descriptivo.

---

---

### Contacto (pages/contact.html)

El diseño de esta página es libre — elegí el layout que mejor se adapte a la identidad visual de tu sitio. Lo que sí son **requisitos estrictos** son las dos primeras secciones:

#### 1. Formulario de contacto (obligatorio)

Un formulario con los siguientes campos:

| Campo | Tipo | Obligatorio |
|-------|------|-------------|
| Nombre completo | `text` | ✅ |
| Correo electrónico | `email` | ✅ |
| Mensaje | `textarea` | ✅ |

**Validaciones requeridas:**
- Todos los campos obligatorios deben tener el atributo `required`
- El email debe tener `type="email"`
- El textarea debe tener un `minlength` razonable (mínimo 20 caracteres) y un `maxlength` para evitar mensajes excesivamente largos (por ejemplo, 1000 caracteres)

#### 2. Mapa (obligatorio)

Embed de Google Maps con la ubicación del negocio mediante un `<iframe>`. Para obtenerlo:

1. Abrí [Google Maps](https://maps.google.com)
2. Buscá una dirección cualquiera (puede ser ficticia, acorde al negocio)
3. Hacé clic en **Compartir → Insertar un mapa**
4. Copiá el código del `<iframe>` y pegálo en tu HTML

El iframe debe verse bien en ambas vistas. En mobile no puede desbordar el contenedor ni quedar cortado.

> 💡 Por defecto los `<iframe>` tienen dimensiones fijas en píxeles que no se adaptan al ancho del contenedor. Para hacerlos responsive, podés envolverlos en un `div` con `position: relative` y `padding-bottom: 56.25%` (relación 16:9), y darle al iframe `position: absolute`, `width: 100%` y `height: 100%`. Es la técnica estándar para embeds responsive.

#### 3. Secciones adicionales (opcionales)

Podés agregar una o más secciones para complementar la página de contacto:

- Dirección física con ícono y texto
- Teléfono y horarios de atención
- Email de contacto directo
- Links a redes sociales
- Cards con el equipo de atención al cliente

**En cualquier caso**, el resultado final debe verse cuidado y bien organizado tanto en mobile como en desktop. Una página de contacto mal diseñada genera desconfianza — es una de las páginas más visitadas de cualquier sitio comercial.

---

### Register (pages/register.html)

Formulario de registro con los siguientes campos:

| Campo | Tipo de input | Obligatorio |
|-------|--------------|-------------|
| Nombre completo | `text` | ✅ |
| Correo electrónico | `email` | ✅ |
| Contraseña | `password` | ✅ |
| Repetir contraseña | `password` | ✅ |
| Fecha de nacimiento | `date` | ✅ |
| Provincia o país | `select` | ✅ |
| Observación | `textarea` | No |

**Validaciones requeridas (HTML nativo):**
- Todos los campos obligatorios deben tener el atributo `required`
- El email debe tener `type="email"` para validación de formato
- La contraseña debe tener `minlength` definido (mínimo 6 caracteres recomendado)
- El `select` de provincia debe tener al menos 5 opciones reales

> 💡 En esta entrega la validación es solo con HTML (`required`, `type`, `minlength`, `maxlength`, `pattern`). En la segunda entrega, cuando migremos a React, vamos a reemplazar esto con validaciones programáticas más robustas.

---

### Productos (pages/products.html)

Esta página muestra el catálogo completo de productos del ecommerce.

- Mostrá las mismas cards de productos que creaste en el Home — los datos tienen que ser idénticos
- El layout de las cards debe ser responsive, igual que en el Home

**Sidebar de filtros (opcional):**

Podés agregar un sidebar lateral con filtros (por categoría, por precio, etc.). En esta entrega **no es necesario que los filtros funcionen** — alcanza con que la estructura visual esté presente: los checkboxes, los rangos de precio o los botones que usarías en la segunda entrega para filtrar. El foco acá es el layout y la organización visual de la página.

> 💡 Un layout típico para una página de productos con sidebar es: un contenedor con `display: flex`, donde el sidebar ocupa un ancho fijo o porcentual (20-25%) y la grilla de productos ocupa el resto (`flex: 1`). En mobile, cambiás a `flex-direction: column` para que el sidebar quede arriba o lo ocultás detrás de un botón "Filtros". Mirá cómo lo resuelven los templates de ThemeForest — es uno de los patrones más repetidos en e-commerce.

---

### Detalle de producto (pages/product-detail.html)

Una página estática que muestre el **primer producto** de la lista con toda su información:

- Imagen grande del producto
- Nombre
- Categoría
- Precio
- Descripción completa
- Botón "Agregar al carrito"
- Demás campos que consideres relevantes (fecha de ingreso, características, link a YouTube, etc.)

> 💡 En esta entrega solo el primer producto tiene página de detalle, y es estática (el contenido está escrito directamente en el HTML). En la segunda entrega, cuando tengamos React y React Router, esta página va a ser dinámica: va a leer el `id` de la URL y va a buscar el producto correspondiente en la API.

---

### Administrador de productos (pages/admin-products.html)

Esta página simula el panel de control de un administrador. Tiene dos secciones:

#### Tabla de productos

Una tabla HTML con **al menos 8 filas** (los mismos productos del Home). Columnas requeridas:

| # | Columna | Notas | Obligatorio |
|---|---------|-------|-------------|
| 1 | Foto | Imagen pequeña (`<img>` con `width` fijo) | ✅ |
| 2 | Nombre | | ✅ |
| 3 | Descripción | Opcional | No |
| 4 | Fecha de ingreso | Formato `DD-MM-YYYY` | ✅ |
| 5 | Precio | | ✅ |
| 6 | Acciones | Botones "Editar" y "Borrar" (sin funcionalidad todavía) | ✅ |

Notas: Para que la tabla se vea bien en mobile, podés crear un contenedor ej: `table-responsive` con `overflow-x: auto` que permita hacer scroll horizontal. En desktop, la tabla se muestra completa sin scroll.

#### Formulario de carga de producto (opcional):**

Un formulario para agregar nuevos productos (sin funcionalidad en esta entrega — solo la estructura visual):

| Campo | Tipo |
|-------|------|
| Nombre | `text` |
| Precio | `number` |
| Descripción | `textarea` |
| Categoría | `select` |
| Imagen | `url` |
| Stock | `number` |
| Link de YouTube | `url` | Opional 
| Características | `checkbox` (múltiples opciones) |

> 💡 Los botones "Editar" y "Borrar" no hacen nada en esta entrega. Su presencia es intencional: estás diseñando la interfaz para que cuando agregues la lógica en la segunda entrega, ya tenga el lugar correcto.

---

### Acerca de nosotros (pages/about.html)

Una página libre que debe incluir:

- Información sobre el proyecto
- Información sobre vos como desarrollador/a
- Una frase que represente la empresa
- Una card o div con tu foto o avatar, tu nombre y algún dato de contacto

El diseño es completamente libre.

---

## Criterios de evaluación

| Criterio | Descripción |
|----------|-------------|
| **Responsive** | El sitio se ve y funciona bien en mobile, tablet y desktop |
| **Cumplimiento de requisitos** | Todas las páginas y secciones están presentes |
| **Semántica HTML** | Uso correcto de etiquetas (`<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<footer>`, etc.) |
| **Código limpio** | HTML semántico, CSS organizado, indentación correcta |
| **Coherencia de datos** | Los productos son los mismos en todas las páginas |
| **Diseño** | El sitio tiene una identidad visual coherente: paleta de colores consistente, tipografía legible y jerarquía visual clara en todas las páginas |
| **Validación Formularios** | Los formularios tienen las validaciones HTML requeridas (`required`, `type`, `minlength`, `maxlength`, `pattern`, etc.) |
