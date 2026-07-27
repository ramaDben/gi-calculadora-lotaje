# Calculadora de lotaje · Grupo Inteligencia

Herramienta pública en pesos chilenos para los activos operables en **Grupo Inteligencia SpA**.

**→ https://bbenja11.github.io/gi-calculadora-lotaje/**

Responde dos preguntas:

- **Cuánto vale el movimiento**: dado un activo y un volumen, cuánto gana o pierde la posición por
  cada tramo de precio (1 punto, 10 puntos, el movimiento que se indique y el recorrido típico de un
  día), más el margen que inmoviliza.
- **Cuántos lotes operar**: al revés, dado un riesgo máximo en pesos y una distancia de stop, el
  volumen que corresponde, ajustado al mínimo que acepta el broker.

## Cómo se calcula

Las cifras no se derivan a mano: las entrega el terminal MetaTrader 5 con `order_calc_profit`, que
aplica el tamaño de contrato, la moneda de cotización de cada instrumento y la conversión a la
moneda de la cuenta. Eso cubre correctamente los casos que se prestan a error: pares con el dólar
como base, metales, índices, un índice europeo que cotiza en euros y CFDs de acciones.

El recorrido típico del día es el ATR de 14 sesiones diarias.

## Sobre los datos

Los valores corresponden al momento indicado en la propia página. El valor de cada movimiento
cambia cuando cambia el precio del activo y cuando cambia el dólar, así que la página se regenera
periódicamente con datos frescos.

`index.html` es un **archivo generado**: no editarlo a mano. Se produce con
`scripts/generar_calculadora.py` del repositorio interno del proyecto, a partir de una plantilla y
de los datos que devuelve el terminal. Todo va autocontenido en un solo archivo, incluidas las
tipografías, para que la página no dependa de ningún servicio externo.

## Aviso

Contenido informativo. Los CFD son instrumentos complejos y presentan un riesgo elevado de perder
dinero rápidamente debido al apalancamiento. Esto no constituye asesoría financiera ni una
recomendación de inversión.
