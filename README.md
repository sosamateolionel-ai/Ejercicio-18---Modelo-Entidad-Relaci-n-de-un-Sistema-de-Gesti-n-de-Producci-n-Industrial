# Ejercicio 18 - Modelo Entidad-Relación de un Sistema de Gestión de Producción Industrial

## Descripción
Este ejercicio consiste en diseñar un modelo Entidad-Relación (DER) para un sistema de gestión de producción industrial y control de calidad. El modelo permite administrar artículos, estructuras de lista de materiales (BOM), líneas de montaje, empleados, órdenes de fabricación e inspecciones de calidad.

## Entidades y atributos

### 1. Articulo
Representa los productos, piezas o componentes fabricados o utilizados en la planta.
- **id_articulo**: identificador único del artículo.
- **nombre comercial**: nombre comercial del artículo.
- **descripcion tecnica**: especificaciones técnicas del componente.
- **tiempo estandar fabricado**: tiempo estimado de producción.

### 2. Estructura bom
Entidad asociativa que define la estructura de ensamblaje (Bill of Materials) descomponiendo los artículos en componentes padres e hijos.
- **codigo artugio hijo**: identificador del componente o pieza componente.
- **codigo artugio padre**: identificador del artículo principal o ensamblaje.
- **cantidad necesaria**: unidades del componente requeridas para el ensamblaje.

### 3. Empleado
Representa al personal operativo y de supervisión de la planta.
- **id_empleado**: identificador único del empleado.
- **dni**: documento nacional de identidad.
- **nombre**: nombre y apellido del empleado.
- **legajo**: número de legajo laboral.
- **cargo principal**: puesto o función del empleado.

### 4. Linea montaje
Representa las líneas de producción o sectores de ensamblaje industrial.
- **id_linea**: identificador único de la línea de montaje.
- **descripcion**: detalle de la línea.
- **id_supervisor**: identificador del empleado supervisor a cargo.

### 5. Orden fabricacion
Representa las órdenes de producción programadas en las líneas de montaje.
- **id_orden**: identificador único de la orden.
- **numero orden**: número oficial de la orden de fabricación.
- **codigo artugio**: código del artículo a producir.
- **id_linea**: identificador de la línea de montaje asignada.
- **fecha emision**: fecha de generación de la orden.
- **estado**: estado actual de la orden (ej. pendiente, en proceso, finalizada).
- **cantidad planificada**: número de unidades a fabricar.

### 6. Inspeccion calidad
Representa las revisiones y controles de calidad aplicados a las órdenes de fabricación.
- **id_inspeccion**: identificador único de la inspección.
- **numero orden**: número de la orden inspeccionada.
- **id_inspector**: identificador del empleado inspector.
- **fecha hora**: marca temporal de la inspección.
- **estado**: resultado de la revisión (ej. aprobado, rechazado).
- **motivo fallo**: causa o detalle del defecto en caso de no superar la prueba.

## Relaciones y cardinalidades
- **Articulo – Estructura bom (Usa / 1:N)**: un artículo puede descomponerse en múltiples componentes o formar parte de varias estructuras de ensamblaje.
- **Linea montaje – Empleado (Opera / 1:1)**: una línea de montaje es operada o supervisada directamente por personal asignado.
- **Articulo – Orden fabricacion (Tiene / 1:N)**: un artículo genera diversas órdenes de fabricación a lo largo del tiempo.
- **Linea montaje – Orden fabricacion (Tiene / 1:N)**: una línea de montaje ejecuta múltiples órdenes de producción.
- **Orden fabricacion – Inspeccion calidad (Cumple / 1:N)**: una orden de fabricación es sometida a una o varias inspecciones de control de calidad.
- **Empleado – Inspeccion calidad (Realiza / 1:N)**: un empleado con rol de inspector realiza las revisiones de calidad.

## Objetivo
Diseñar una base de datos para una planta industrial que permita administrar el catálogo de artículos y sus estructuras de despiece (BOM), gestionar el personal y las líneas de montaje, programar y controlar las órdenes de fabricación, y llevar un registro riguroso de los controles e inspecciones de calidad de los productos.
