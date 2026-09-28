# gsdistribuidor.com: arreglo de duplicados

Problemas vistos en el índice de Google (búsqueda `site:gsdistribuidor.com`, sept. 2026):

1. Productos con dos prefijos: `/producto/...` y `/product/...`.
2. Sculptra indexado 3 veces: `/producto/sculptra/`, `/producto/sculptra-sanofi/`, `/product/sculptra-sanofi/`.
3. Etiquetas de producto (`/product-tag/...`), etiquetas del blog (`/tag/...`) y archivos por fecha (`/2023/12/`, `/2024/01/`) indexados.

## 1. Unificar las URLs de producto (301)

Usa `redirecciones.htaccess` (instrucciones dentro del archivo).
Alternativa sin tocar archivos: plugin **Redirection** con una regla regex
`^/product/(.+)$` → `/producto/$1` (o al revés según la base que uses).

Comprueba después abriendo una URL vieja: debe saltar a la nueva, no mostrar la página ni un 404.

## 2. Sacar del índice etiquetas y fechas (noindex)

Solo con el plugin SEO que uses (debe haber **uno solo** activo):

- **All in One SEO**: Apariencia en buscadores > Taxonomías > Etiquetas de producto y Etiquetas >
  "Mostrar en resultados de búsqueda" = No. En Archivos > Archivos por fecha = No (o desactivarlos).
- **Yoast**: Ajustes > Taxonomías > Etiquetas de producto / Etiquetas > "Mostrar en resultados" = Off.
  Ajustes > Avanzado > Archivos por fecha = Off.
- **Rank Math**: Títulos y Meta > Etiquetas de producto / Etiquetas > Robots Meta = No Index.
  Títulos y Meta > Otros > Archivos por fecha = desactivar.

No borres las etiquetas: se siguen usando para filtrar en la tienda, solo dejan de indexarse.

## 3. Limpiar caché y avisar a Google

1. SiteGround: Site Tools > Speed > Caching > Purgar caché (y el plugin SG Optimizer).
2. Search Console > Sitemaps: reenviar `https://gsdistribuidor.com/sitemap.xml`.
3. Search Console > Inspección de URL: pedir indexación de las fichas finales de producto.
4. En 2-4 semanas revisar Páginas > "Duplicada, Google eligió una canónica diferente".
