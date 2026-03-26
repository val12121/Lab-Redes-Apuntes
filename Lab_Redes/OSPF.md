# P05. Redistribución de rutas

Para la práctica de hoy. El concepto de redistribución de rutas se refiere al hecho de que un protocolo de enrutamiento pueda obtener información de distintas fuentes y distribuirla en su dominio de enrutamiento

Las posibles fuentes a considerar serían:

- Rutas del propio dominio de enrutamiento: Se distribuyen siempre.    
- Rutas estáticas.
- Rutas de otros protocolos de pasarela interior.    
- Rutas externas al sistema autónomo.

hay casos en los que es necesario el uso de más de un protocolo de enrutamiento de pasarela interior dentro de un sistema autónomo.

## Redistribución de rutas de OSPF en RIP:  
`router rip`  
`redistribute ospf metric 1`

Cuando existe una misma ruta para dos protocolos distintos, se utiliza la llamada **ruta administrativa** para decidir cual de las rutas se convierte en la tabla de enrutamiento.

A nivel de comandos la redistribución de rutas se logra de la siguiente manera:  
`router ospf`  
`redistribute rip metric 10000`

En una red con redistribución de rutas, pueden aparecer distintos problemas derivados del uso de distintos costes en distintos protocolos de enrutamiento. **Cada protocolo utiliza costes distintos.** Por ejemplo, RIP utiliza como métrica el número de saltos, mientras que OSPF utiliza una función de coste más elaborada. La búsqueda de rutas óptimas no sería posible si se utilizan directamente los costes asociados a cada protocolo. Esto hace necesaria la definición de una métrica para las rutas redistribuidas que sea compatible con la del protocolo receptor.

Hay que evitar los bucles de redistribución.
