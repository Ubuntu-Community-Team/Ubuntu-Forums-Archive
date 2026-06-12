---
title: "how to install raid on k7vta3 promise"
date: 2006-05-11
forum: Installation &amp; Upgrades
---

### Post by alvaro.uy on 2006-05-11
The explanation is on spanish but if you dont understand pleasse askme

Mi placa es una ECS KTVTA3 con raid promise onboard
Para usar el raid con ubuntu la solucion mas sencilla fue hacerlo por software pero aprovechando los canales para raid de la placa:
Colocar los discos con los que haremos el raid, ambos como master, en cada canal IDE destinado a raid de la placa.
No crear raid por hardware (aunque en el arranque se nos brinda la oportunidad cuando la placa detecta que tiene discos en los ide destinados a raid)
Elegir particionado manual durante el procedimiento de instalacion.

Preparamos los 2 discos para el RAID

En un disco (al que le borramos todas las particiones):
Crear una particion primaria (50MB esta bien) del tipo ext2 con la etiqueta /boot
Crear una particion logica (aprox igual que la RAM, en mi caso 256MB) del tipo intercambio.
Crear una particion logica (con el resto del espacio libre) del tipo raid

En el otro disco:
repetir los pasos anteriores pero la primer particion (la de 50MB) hacerla del tipo "no usar'' en vez de ext2

Ahora creamos el raid

Elegimos la opcion crear raid y marcamos los discos que usaremos, aplicamos los cambios.
Formateamos la nueva unidad que nos aparece (resultado de la union de las particiones raid anteriores) usamos todo el espcio disponible y la formatemos del tipo ext3 con la etiqueta /

Ya esta listo para instalarse el ubuntu :)

La idea es que el sistema hara RAID con la particion / que es donde residen todos los datos y programas, con esto obtendremos la mejoras asociadas al raid
La particion /boot no puede estar en el raid pues es la que define al raid (no puede ser juez y parte)
La particion Swap no necesita estar en el raid pues ya estara en dos discos distintos y linux hace el balanceo de cargas automaticamente

Recordar desabilitar el raid por hardware si esta habilitado, en mi caso ctrl f cuando la maquina lo solicita en el arranque

---

