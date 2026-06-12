---
title: "[SOLVED] Problem with apt-get and pcmanfm"
date: 2008-06-27
forum: Installation &amp; Upgrades
---

### Post by piousp on 2008-06-27
OK, i was trying out LXDE. I used aptitude instead of apt-get to install it. After a while, i decided to remove it, so again, i used aptitude.

Everything looked fine, until i tried to install new upgrades to my system.
Apparently, there is an error with the package pcmanfm; it says that the package its a so bad state, that it cant be removed, and i need to re-install it. Thats were i get lost.

Here is the output of my terminal:

```
piousp@SPQR:~$ sudo apt-get upgrade
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  libakonadiprivate0 pcmanfm xserver-xorg-video-amd xserver-xorg-video-geode
  xserver-xorg-video-nsc
5 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
1 no instalados del todo o eliminados.
Se necesita descargar 0B/989kB de archivos.
Se utilizarán 1130kB de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? S
AVISO: ¡No se han podido autenticar los siguientes paquetes!
  pcmanfm libakonadiprivate0
¿Instalar estos paquetes sin verificación [s/N]? s
Seleccionando el paquete pcmanfm previamente no seleccionado.
(Leyendo la base de datos ...
dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`pcmanfm', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

154170 ficheros y directorios instalados actualmente.)
Preparando para reemplazar pcmanfm 0.4.1.1-4~lxde (usando .../pcmanfm_0.4.1.1-4~lxde_i386.deb) ...
Updating mime-database
Updating desktop-database
/var/lib/dpkg/tmp.ci/preinst: 32: update-desktop-database: not found
dpkg: error al procesar /var/cache/apt/archives/pcmanfm_0.4.1.1-4~lxde_i386.deb (--unpack):
 el subproceso pre-installation script devolvió el código de salida de error 127
Updating mime-database
Updating desktop-database
/var/lib/dpkg/tmp.ci/postrm: 34: update-desktop-database: not found
dpkg: error al reorganizar:
 el subproceso post-removal script devolvió el código de salida de error 127
Se encontraron errores al procesar:
 /var/cache/apt/archives/pcmanfm_0.4.1.1-4~lxde_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


And here is a rough translatin of it from google translate (just in case ;) )

```
piousp SPQR @: ~ $ sudo apt-get upgrade
Reading package list ... Made
Creating dependency tree
Reading the status information ... Made
It updated the following packages:
   libakonadiprivate0 pcmanfm xserver-xorg-video-amd xserver-xorg-video-Geode
   xserver-xorg-video-nsc
5 updated, will be installed 0, 0 and 0 to eliminate not updated.
1 not fully installed or removed.
0B/989kB is needed to download files.
1130kB will be used for additional disk space after unpacking.
Do you want to continue [S / N]? S
Warning: Failed to authenticate the following packages!
   pcmanfm libakonadiprivate0
Can Install these packages without verification [s / N]? s
Selecting the package pcmanfm not previously selected.
(Reading database ...
dpkg: important warning: missing files list files package
`pcmanfm 'will mean that the package has no file
currently installed.

154170 files and directories currently installed.)
Preparing to replace pcmanfm 0.4.1.1-4 ~ lxde (using .../pcmanfm_0.4.1.1-4 ~ lxde_i386.deb) ...
Updating mime-Database
Updating desktop-Database
/ var / lib / dpkg / tmp.ci / preinst: 32: update-desktop-database: not found
dpkg: error processing / var/cache/apt/archives/pcmanfm_0.4.1.1-4 ~ lxde_i386.deb (- unpack):
  Thread pre-installation script returned code output error 127
Updating mime-Database
Updating desktop-Database
/ var / lib / dpkg / tmp.ci / postrm: 34: update-desktop-database: not found
dpkg: error while reorganizing:
  Thread post-removal script returned code output error 127
There were errors in processing:
  / var/cache/apt/archives/pcmanfm_0.4.1.1-4 ~ lxde_i386.deb
E: Sub-process / usr / bin / dpkg returned an error code (1)
```

---

### Post by Pumalite on 2008-06-27
Try:
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get --configure -a
sudo apt-get -f install
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by piousp on 2008-06-30
Thanks for the quick reply!
But none of them solve my problem, any more ideas?
By the way, apt-get --configure -a does not work. I tried dpgk --configure -a instead.

---

### Post by Pumalite on 2008-06-30
Sorry about that. It is sudo dpkg --configure -a
What was the output?

---

### Post by piousp on 2008-07-01
At first, it gave some errors. But i dont know, after a while, it stopped given me errors!
Thanks for your help!
Now, where is that "mark as solved" option?

---

### Post by Pumalite on 2008-07-01
You are welcome.

---

