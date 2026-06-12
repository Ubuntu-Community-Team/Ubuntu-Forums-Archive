---
title: "Ubuntu 9.10 upgrade problem/Problema al actualizar Ubuntu 9.10"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by wcruzy on 2010-09-25
Dear Sirs:

I have the following problem when trying to update or download a package in Ubuntu 9.10:


dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 21906:
 nombre de paquete inválido (
E: Sub-process /usr/bin/dpkg returned an error code (2)


I reinstalled Ubuntu and the message still appears

I hope some advice from you.

Sincerely,

Wilfredo Cruz Y




Estimados señores:

Tengo el siguiente problema al tratar de actualizar o descargar un paquete en Ubuntu 9.10:


dpkg: error en el análisis, en archivo «/var/lib/dpkg/available» línea cercana 21906:
 nombre de paquete inválido (
E: Sub-process /usr/bin/dpkg returned an error code (2)


He reinstalado el Ubuntu y el mensaje sigue apareciendo

Espero un consejo de parte de ustedes.

Atentamente,

Wilfredo Cruz Y

---

### Post by Rubi1200 on 2010-09-25
If you run ```
sudo dpkg --configure -a
``` in the terminal what error messages do you get?

---

### Post by wcruzy on 2010-09-26
Gracias por el consejo.

He probado con apt-get install -f

y con el comando dpkg --configure -a

el problema se presenta varias veces y no permite realizar instalaciones como del netbeans 6.9 y otros

Seguiré intentando

Nuevamente muy agradecido

---

### Post by Rubi1200 on 2010-09-26
Sorry, this forum is English only.

From what I did understand you are trying to install netbeans?

Please try and tell us in English, as best you can, what is going wrong.

Alternatively, Google for an Ubuntu forum in your language (I am sure there must be one).

---

### Post by mwildam on 2010-09-27
If NetBeans is the problem, you might have installed the v6.9 by hand/manually already before your upgrade process after installing NetBeans first through the repositories.

I guess you did not uninstall NetBeans through the repositories before installing it manually.

Basically I do never install NetBeans through the repositories (using apt or synaptic) because I usually get problems then with the built-in update feature within NetBeans and second, because I usually want to have the recent NetBeans version on my system.

In the repositories of 10.04 there is still the version 6.8 of NetBeans (and current is 6.9.1 at this time).

Try to uninstall NetBeans through repositories/package management.

For a manual installation you could do it like I do -  see [http://it-tactics.blogspot.com/2010/09/install-netbeans-on-ubuntu-1004.html](http://it-tactics.blogspot.com/2010/09/install-netbeans-on-ubuntu-1004.html)

---

