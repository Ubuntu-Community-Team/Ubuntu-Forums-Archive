---
title: "GCC-4.5 Installation problem"
date: 2016-05-22
forum: Installation &amp; Upgrades
---

### Post by petrus2 on 2016-05-22
Hi
I have with Windows 7 like host a virtual machine Vbox with Ubuntu 14.04, to use with OpenFoam (CFD software). With the versión 2.2.1 it worked perfect,  but I wanted install the old versión 1.7.1 because of a misunderstood mistake with a mesh. Anyway, I followed the  instruction from here [http://openfoam.org/download/1-7-1-ubuntu/](http://openfoam.org/download/1-7-1-ubuntu/), but I dunno what I did wrong that I couldn’t install the version, plus I uninstalled the version 2.2.1. So after that, always I opened the consola I got this message:
[COLOR=#ff0000](Image 1)
[/COLOR]*No existe el archive o directorio:* **The file or directory doesn’t exist**.
I deleted all folders of OpenFoam and I started to install it from other link, [https://openfoamwiki.net/index.php/Installation/Linux/OpenFOAM-1.7.1/Ubuntu](https://openfoamwiki.net/index.php/Installation/Linux/OpenFOAM-1.7.1/Ubuntu). But when I trying to install the library gcc-4.5 I get always this error. *sorry for the spanish, I dunno how change it to English, but here translating the sentences.
[COLOR=#ff0000](Images 2 y 3)[/COLOR]
•          Leyendo lista de paquetes... Hecho: reading lists of package…Done
•          Creando árbol de dependencias: creating dependence tree
•          Leyendo la información de estado... Hecho: reading the state info…Done
•          No se pudieron instalar algunos paquetes. Esto puede significar que usted pidió una situación imposible o, si está usando la distribución inestable, que algunos paquetes necesarios no han sido creados o han sido movidos fuera de Incoming: Some packages couldn’t be installed. It might meaning you have requested an imposible situation or, if using the distribution unstable that some required package haven’t been created or been  moved out of incoming.
•          La siguiente información puede ayudar a resolver la situación: the following info can help you to resolve the situation
•          Los siguientes paquetes tienen dependencias incumplidas: The following packages have unmet dependencies
•          Depende: depend
•          Pero no va a instalarse: but it won’t be install
•          Resolve generó cortes, esto puede haber sido causado por paquetes retenidos: Resolve generated cuts, it may have been caused by held packages.
I have tried to install old and last versions, to repare the broken packages with the Synaptic option
[COLOR=#ff0000](Image 4)
[/COLOR]Also I tried the instruction in this link, but I dunno how identified the rebel package to delete the lines [http://www.adslzone.net/postt290764.html](http://www.adslzone.net/postt290764.html)
Also have tried  apt-get update; apt-get upgrade… as this link [http://askubuntu.com/questions/154402/install-gcc-on-ubuntu-12-04-lts/154406](http://askubuntu.com/questions/154402/install-gcc-on-ubuntu-12-04-lts/154406)
Also to install build-essential, getting the same error plus I couldn’t sharing folder with the host anymore, so I unistalled it.
Also apt-get autoremove, dist-update, dist-upgrade from this list  which I found, [http://www.preguntaslinux.org/-howto-apt-y-aptitude-t-5780.html](http://www.preguntaslinux.org/-howto-apt-y-aptitude-t-5780.html) and nothing.
 
Also I read this one [http://www.ubuntu-es.org/node/74339#.VzKfjISLSM8](http://www.ubuntu-es.org/node/74339#.VzKfjISLSM8), in which he delating and reinstalling the two package which had dependence, but I have a lot!!
By last I get in of sudo gedit /var/lib/dpkg/status like i saw at [http://www.adslzone.net/postt293517.html](http://www.adslzone.net/postt293517.html) but the file is enormous and I dunno well what I’m looking for.

---

