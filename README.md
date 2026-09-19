# 🚗 Movilidad Urbana y Productividad Económica en Ciudades de LATAM (2024)

> 👤 **Rol:** Analista de Datos en el *American Development Bank* (Proyecto Individual)  
> 🏢 **Contexto:** Caso de Negocio / Proyecto de Portafolio (Bootcamp Analytics - Proyecto 5)  
> 🎯 **Alcance:** Integración y limpieza de datasets (`tomtom_traffic.csv` + `oecd_city_economy.csv`), estandarización de formatos, filtrado del año 2024, agregación dimensional por ciudad-año, análisis exploratorio visual (EDA) en Python y elaboración de informe ejecutivo.  
> 🛠️ **Stack Técnico:** Python (`pandas`, `numpy`, `seaborn`, `matplotlib`), Jupyter Notebook.

---

## 🎯 Contexto y Objetivo del Proyecto

Como analista de datos en el **American Development Bank**, el equipo debe entregar un reporte para comprender cómo la **movilidad urbana** (niveles de congestión, tiempos de viaje, retrasos) se relaciona con la **productividad económica** (PIB per cápita, desempleo) en las principales ciudades de América Latina durante el año **2024**.

El objetivo central del banco es identificar en qué ciudades es prioritario investir en infraestructura de transporte para aumentar la productividad y el bienestar de la población, respondiendo a tres preguntas de negocio:
1. ¿Qué ciudades presentan alta congestión y baja productividad económica?
2. ¿Cuáles muestran los mejores indicadores combinados (movilidad eficiente y economía fuerte)?
3. ¿Qué variables parecen tener una relación más fuerte con el desarrollo urbano?

---

## 📂 Fuentes de Datos

El análisis utiliza dos fuentes de datos reales del año 2024:
* `tomtom_traffic.csv`: Datos sobre congestión vehicular y condiciones de tráfico en tiempo real recopilados por TomTom (múltiples registros puntuales por ciudad).
* `oecd_city_economy.csv`: Indicadores anuales sobre economía urbana, empleo, contaminación y población recopilados por la OECD (Organización para la Cooperación y el Desarrollo Económicos)


Cada registro corresponde a una actualización puntual del estado del tráfico en una ciudad.
---

## ⚙️ Plan de Acción y Flujo de Trabajo en Python

El proceso se desarrolló de forma programática en un **Jupyter Notebook** siguiendo estos pasos:

1. **Carga y Exploración Inicial:** Identificación de columnas, tipos de datos y estructura general de los archivos.
2. **Limpieza y Corrección de Formatos:**
   * Conversión de columnas de fecha a `datetime64`.
   * Limpieza de separadores numéricos (puntos y comas) y eliminación de símbolos de porcentaje.
   * Transformación de variables económicas de tipo `object` a `float64` para permitir cálculos.
3. **Filtrado y Agregación (Año 2024):**
   * Filtrado exclusivo del período 2024.
   * Cálculo de promedios anuales de métricas de tráfico (`JamsDelay`, `TrafficIndexLive`, `TravelTimeLivePer10KmsMins`) para consolidar los múltiples registros diarios por ciudad.
4. **Integración de Datasets (Unión INNER JOIN):**
   * Combinación de las tablas de tráfico (TomTom) y economía (OECD) manteniendo únicamente las ciudades presentes en ambas fuentes con información completa.
   * Cobertura final: 15 ciudades latinoamericanas en 7 países (Argentina, Brasil, Chile, Colombia, México, Perú y Uruguay).
5. **Validación y Análisis Visual:**
   * Desarrollo de boxplots de congestión (`JamsDelay`), histogramas de PIB per cápita y gráficos de barras comparativos entre variables económicas y de movilidad.
6. **Exportación:** Generación del dataset unificado y depurado.

---

## 📊 Resumen Ejecutivo e Insights Clave

### 🔍 Hallazgos Principales

* **Mito Desmentido ("Más dinero = menos tráfico"):** No existe una correlación lineal directa entre el PIB per cápita y los niveles de congestión vehicular. Ser una ciudad con mayor riqueza no garantiza una mejor movilidad.
* **Ciudad de México (Congestión Crítica):** Presenta el retraso por congestión más extremo de la muestra (**2,833 minutos**) con un PIB per cápita de **$11,442 USD**, representando un impacto masivo en la población.
* **Brasilia (Modelo de Éxito):** Destaca como caso excepcional con un PIB per cápita alto (**$16,251 - $23,456 USD**) y la congestión más baja de la muestra (**101 minutos**). Su diseño urbano planificado demuestra que la planificación inteligente supera a la sola riqueza económica.
* **Infraestructura vs. Población:** La densidad poblacional por sí sola no determina el tráfico. Buenos Aires (15.4M hab.) maneja mejor la circulación que Bogotá (11.3M hab. con 1,141 min de retraso), lo que sugiere que la calidad de la infraestructura de transporte es más determinante que el tamaño de la población.

---

## 💡 Recomendaciones de Inversión para el Banco

### 📈 Priorización de Ciudades para Infraestructura
* **Prioridad Alta (Ciudad de México):** Intervención urgente requerida debido al nivel crítico de congestión (2,833 minutos de retraso) y la gran afectación a la población.
* **Prioridad Alta (Bogotá):** Presenta el mejor retorno potencial de inversión (ROI), al combinar un nivel de congestión moderadamente alto (1,141 minutos) con un PIB per cápita de $11,442 USD.
* **Prioridad Media (Lima):** Presenta 892 minutos de retraso, representando una oportunidad clara de mejora antes de llegar a niveles extremos.

### 📋 Acciones Estratégicas
1. **Desarrollar análisis de impacto económico detallado** enfocado en Ciudad de México y Bogotá.
2. **Replicar el modelo de planificación urbana de Brasilia**, aprovechando su caso de éxito en baja congestión y alto PIB per cápita.

---

## 🖼️ Visualizaciones del Proyecto

Todas las visualizaciones fueron generadas directamente en el **Jupyter Notebook** utilizando `matplotlib` y `seaborn`:

* **Boxplot de Congestión:** Evaluación de la distribución y dispersión de retrasos (`JamsDelay`).
* **Histograma de PIB per Cápita:** Análisis de la distribución de la riqueza urbana en las ciudades evaluadas.
* **Gráficos de Barras Comparativos:** Análisis cruzado entre variables de movilidad y desempeño económico.

---

## 📁 Estructura del Repositorio

```text
├── visualizaciones/                                    <- Gráficos y visualizaciones (.png) del EDA
│   ├── 01_boxplot_congestion.png
│   ├── 02_scatter_gdp_vs_traffic.png
│   └── 03_ranking_ciudades_prioritarias.png
├── data/                                                <- Fuentes de datos 
│   ├── tomtom_traffic.csv                               <- Tráfico transaccional TomTom
│   ├── oecd_city_economy.csv                            <- Macroeconomía OECD 
├── notebook/
│   └── ladb_mobility_economy_project.ipynb              <- Notebook estructurado con limpieza y análisis
└── README.md                                            <- Informe ejecutivo y documentación del proyecto


