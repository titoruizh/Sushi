# Sushi

```mermaid
flowchart TD
  %% Pool: Fukusuke Sushi-Delivery
  subgraph Fukusuke_Sushi_Delivery
    direction TB
    lane_Gerencia["Lane: Gerencia/Jefe de Proyecto"]
    lane_Analista["Lane: Analista de Métricas/PMO"]
    lane_TI["Lane: Equipo TI (Visión por Computadora)"]
    lane_Logistica["Lane: Operación Logística (Despachadores)"]

    %% Fases del proceso
    A1(Inicio del ciclo de Medición y Análisis)
    A2[Definir objetivos y métricas]
    A3[Recolectar datos (OCR, Despacho, Encuestas)]
    A4[Analizar e interpretar datos]
    A5{¿Desvíos u oportunidades de mejora?}
    A6[Planificar y ejecutar acciones de mejora]
    A7[Comunicar hallazgos y resultados]
    A8[Actualizar repositorio de métricas]
    A9(Cierre de ciclo e integración TRP)
    A10(Fin del ciclo / Loop al próximo periodo)

    %% Artefactos
    D1[(Repositorio Métricas)]
    D2[(Reporte Medición/Análisis)]
    D3[(Encuestas Satisfacción)]
    D4[(Sistema OCR)]
    D5[(Módulo Despacho)]
    D6[(Plan de Acción)]

    %% Flujos internos
    lane_Gerencia --> A1
    A1 --> A2
    A2 --> D1
    A2 --> lane_Analista
    lane_Analista --> A3
    A3 --> D4
    A3 --> D5
    A3 --> D3
    A3 --> lane_TI
    lane_TI --> A4
    lane_Analista --> A4
    A4 --> D2
    A4 --> A5
    A5 -->|Sí| A6
    A5 -->|No| A7
    A6 --> D6
    A6 --> lane_Logistica
    lane_Logistica --> A7
    A7 --> D2
    A7 --> D1
    A7 --> A8
    A8 --> D1
    A8 --> A9
    A9 --> D1
    A9 --> A10
    A10 --> A1

  end

  %% Pool externo: Cliente
  subgraph Cliente_App_Web
    direction TB
    C1(Recibe encuesta de satisfacción)
    C2(Envia respuestas / Reclamos)
  end

  %% Mensajes entre pools
  D3 -.-> C1
  C2 -.-> lane_Analista

  %% Notas
  note over A2,A3
    Fase 1: Definir objetivos y métricas
    Incluye: Tiempo de entrega, precisión OCR, satisfacción cliente (escala 1-10)
  end

  note over A4,A5
    Fase 2: Análisis e interpretación de datos
    Frecuencia: Mensual
  end

  note over A6
    Fase 3: Implementar acciones de mejora si hay desvíos
  end

  note over A7,A8,A9,A10
    Fase 4: Comunicación, actualización y cierre de ciclo
    Integración con otros procesos TRP
  end
```
