# Scoring-de-Riesgo

## Vision general del proyecto
Dentro de un dataset de prestamos personales se creara un modelo para calcular la perdida esperada  de un cliente,  en caso de que deje de pagar  un préstamo dado
Se utilizara el enfoque bancario
Expected Loss = Probability of Default * Principal * Exposure at Default * Loss Given Default


## ¿Que se puede lograr con estos datos?
Se calculara la probabilidad de que ocurra el impago, y además se calculara el impacto económico de ese impago

## Calidad de datos y EDA
Se realizan imputaciones, eliminaciones de registros con valores atipicos y correcciones de los datos, 
se llegan a las conclusiones que la variable target la vamos a tener que crear nosotros

![Variables Categoricas](https://github.com/vidalrl/Scoring-de-Riesgo/blob/main/imagenes/graficas%20variables%20categoricas.png)

![Variables Numericas](https://github.com/vidalrl/Scoring-de-Riesgo/blob/main/imagenes/graficas%20variables%20numericas.png)

## Construccion del modelo
- Se crean tres modelos para poder construir las target  Probability of Default(Regresion logistica), Exposure at Default(Regresion lineal), Loss Given Default(Regresion lineal)
- Para el modelo de Probability of Default, se crea la variable target con un valor de 1 para los clientes que tengan de estado: Default, charged off y does not meet criteria policy: charged off" y todos los demas con valor de 0, y eliminamos la variable estado
- Para el modelo de EAD, creamos la variable pendiente, para saber el monto pendiente del prestamo total al momento que se haga el default en porcentaje
- Para el modelo de el LGD  se construye la target tambien en porcentaje, del monto que no se pudo recuperar en caso de un impago
- Se construyen 3 pipelines, preprocesamiento, entrenamiento y ejecucion para produccion
