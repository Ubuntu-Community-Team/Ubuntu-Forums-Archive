---
title: "blank screen post instalacion 8.04 amd64"
date: 2008-04-29
forum: Installation &amp; Upgrades
---

### Post by hugorodri on 2008-04-29
hola! soy nuevo con ubuntu... mas bien, quiero ser nuevo con ubuntu. Intente con linux hace 15,10 y 5 (años). Quiero que esta sea la ultima!!!!

Instale ubuntu studio en una amd64. Termino todo ok. Pero... al iniciar, luego de seleccionar ubuntu, se pone la pantalla negra y suena un beep. Despues de eso nada mas.

Leyendo encontre x todos lados ese problema, parece ser de video. Hice algo de lo que lei (cambiar splash x vga=normal) pero nada. POR FAVOR!!!! ALGUNO DE ESOS (que son muchos) QUE LA TIENEN RECLARA me podrian dar una mano?

SIENTO QUE ESTOY MUY CERCA DE DECIRLE **** u' a WINDOWS!!! AYUDENME!!!


Tengo amd64, 1.5 G, disco (para ubuntu) 60, comparto disco 160 con XP. mother ASUS M2N-VM DVI

---

### Post by Pumalite on 2008-04-29
Did you install the driver for your card?
If not:
sudo dpkg-reconfigure xserver-org
Accept most defaults, choose vesa as the driver. Once IN the system; install appropriate drivers.

---

### Post by hugorodri on 2008-04-29
hola! probe con sudo dpkg-reconfigure xserver-org y solo me muestra la configuracion del teclado... gracias

---

