# 📈 Predicción de Precios Stock con LSTM (Multivariado)

Este repositorio contiene un script en Python que entrena un modelo de red neuronal LSTM para predecir precios de acciones utilizando datos históricos descargados desde Yahoo Finance.

Incluye:

- Descarga dinámica de datos del activo (por defecto: MSTR)
- Cálculo de indicadores técnicos como retorno diario y RSI
- Construcción de dataset con ventanas deslizantes
- Entrenamiento de un modelo LSTM multivariado
- Evaluación con RMSE y visualización de resultados
- Predicción del precio para el siguiente día hábil real

---

## 📦 Requisitos

Instala las siguientes dependencias antes de ejecutar el script:

```bash
pip install yfinance ta tensorflow pandas matplotlib scikit-learn
```

---

## 🚀 Cómo usar

1. Ejecuta el script `lstm_prediccion.py` en un entorno Python (Colab, Jupyter o local).
2. Modificar el valor del ticker si se desea analizar otro activo.
3. El modelo descargará datos de los últimos 3 años automáticamente.
4. Al final, se mostrará el gráfico de predicción y la predicción para el próximo día hábil.

---

## 🧠 Fundamento

El modelo utiliza una arquitectura LSTM de dos capas, entrenada con secuencias de 15 días (ventanas) que contienen:

- **Precio de cierre (`price`)**: refleja la evolución directa del valor del activo.
- **Retorno diario (`return_1`)**: representa el cambio porcentual entre días consecutivos. Esta variable aporta información sobre la **dirección y magnitud del movimiento reciente**, ayudando al modelo a detectar momentum.
- **RSI (`rsi`)**: es un indicador técnico que mide la fuerza relativa del precio y ayuda a identificar **posibles zonas de sobrecompra o sobreventa**. Incorporarlo permite que el modelo tenga una señal de **contexto técnico**, utilizada frecuentemente por analistas humanos.

La combinación de estas tres variables busca ofrecer al modelo tanto información bruta (precio), como **derivada** (retornos) y **sintetizada** (RSI), para mejorar su capacidad de generalización.

---

## 📊 Ejemplo de salida

```text
🔍 RMSE para MSTR: 4.12
📅 Predicción para 2025-03-27: $425.68
```

---

## 📁 Estructura del proyecto

```
prediccion-lstm-precios-stock/
├── lstm_prediccion.py         # Script principal con comentarios en español
└── README.md
```

---

## ✍️ Autor

Este proyecto fue desarrollado como ejercicio práctico para el modelado de series temporales con redes neuronales LSTM.

---
