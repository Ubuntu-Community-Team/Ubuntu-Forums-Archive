---
title: "Can't install anything !!"
date: 2008-08-01
forum: Installation &amp; Upgrades
---

### Post by badgandalf on 2008-08-01
Hope you can help. I got a broken package problem some days ago that I've been trying to resolve following several advise I found on the forums. However, I probably did something wrong and now apt-get does not work at all. Whenever I try to install something I get the following error:

ignacio@atico:~$ sudo aptitude install dpkg

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se configurarán los siguientes paquetes que están ahora parcialmente instalados:
  libapache2-mod-php5 php5 php5-cgi php5-mysql
0 paquetes actualizados, 0 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B de ficheros. Después de desempaquetar se usarán 0B.
Escribiendo información de estado extendido... Hecho
Configurando libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar libapache2-mod-php5 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Configurando php5-cgi (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar php5-cgi (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
dpkg: problemas de dependencias impiden la configuración de php5:
 php5 depende de libapache2-mod-php5 (>= 5.2.4-2ubuntu5.3) | php5-cgi (>= 5.2.4-2ubuntu5.3); sin embargo:
 El paquete `libapache2-mod-php5' no está configurado todavía.
 El paquete `php5-cgi' no está configurado todavía.
dpkg: error al procesar php5 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de php5-mysql:
 php5-mysql depende de phpapi-20060613+lfs; sin embargo:
  El paquete `phpapi-20060613+lfs' no está instalado.
  El paquete `libapache2-mod-php5' que provee `phpapi-20060613+lfs' aún no está configurado.
  El paquete `php5-cgi' que provee `phpapi-20060613+lfs' aún no está configurado.
dpkg: error al procesar php5-mysql (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 libapache2-mod-php5
 php5-cgi
 php5
 php5-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando php5-cgi (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar php5-cgi (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Configurando libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar libapache2-mod-php5 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
dpkg: problemas de dependencias impiden la configuración de php5:
 php5 depende de libapache2-mod-php5 (>= 5.2.4-2ubuntu5.3) | php5-cgi (>= 5.2.4-2ubuntu5.3); sin embargo:
 El paquete `libapache2-mod-php5' no está configurado todavía.
 El paquete `php5-cgi' no está configurado todavía.
dpkg: error al procesar php5 (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de php5-mysql:
 php5-mysql depende de phpapi-20060613+lfs; sin embargo:
  El paquete `phpapi-20060613+lfs' no está instalado.
  El paquete `libapache2-mod-php5' que provee `phpapi-20060613+lfs' aún no está configurado.
  El paquete `php5-cgi' que provee `phpapi-20060613+lfs' aún no está configurado.
dpkg: error al procesar php5-mysql (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 php5-cgi
 libapache2-mod-php5
 php5
 php5-mysql
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho

Is there anyone who can help? Thnks a lot,

Ignacio

---

### Post by oldos2er on 2008-08-01
Have you tried running "sudo apt-get install -f"?

---

### Post by badgandalf on 2008-08-02
Yep. No result. Ignacio

---

### Post by meindian523 on 2008-08-02
Translate please?

---

### Post by falkTX on 2008-08-02
Just run in terminal:
sudo dpkg --configure libapache2-mod-php5 php5 php5-cgi php5-mysql

then
sudo apt-get install -f
(you may need to install phpapi-20060613+lfs manually, through "dpkg -i ***.deb")

---

### Post by badgandalf on 2008-08-02
No use with sudo dpkg --configure libapache2-mod-php5 php5 php5-cgi php5-mysql

There you are the result. I'll try to find the .deb you suggested.

[sudo] password for ignacio:
Configurando libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar libapache2-mod-php5 (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
Configurando php5-cgi (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar php5-cgi (--configure):
 el subproceso post-installation script devolvió el código de salida de error 10
dpkg: problemas de dependencias impiden la configuración de php5-mysql:
 php5-mysql depende de phpapi-20060613+lfs; sin embargo:
  El paquete `phpapi-20060613+lfs' no está instalado.
  El paquete `libapache2-mod-php5' que provee `phpapi-20060613+lfs' aún no está configurado.
  El paquete `php5-cgi' que provee `phpapi-20060613+lfs' aún no está configurado.
dpkg: error al procesar php5-mysql (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de php5:
 php5 depende de libapache2-mod-php5 (>= 5.2.4-2ubuntu5.3) | php5-cgi (>= 5.2.4-2ubuntu5.3); sin embargo:
 El paquete `libapache2-mod-php5' no está configurado todavía.
 El paquete `php5-cgi' no está configurado todavía.
dpkg: error al procesar php5 (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 libapache2-mod-php5
 php5-cgi
 php5-mysql
 php5

...and this is the size of the disaster with the manual dpkg -i

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libvisual-0.4-0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`skim', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgsl0ldbl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cupsddk-drivers', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-intel', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`thunderbird-locale-en-gb', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-launchpad-bugs', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`avidemux-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`system-config-printer-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmimelib1c2a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kubuntu-konqueror-shortcuts', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcaca0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`friendly-recovery', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libtar', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`scim-bridge-agent', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-qt3', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`network-manager', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`linux-headers-2.6.24-19-generic', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libhtml-parser-perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`console-terminus', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-qt4', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libc6-i686', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`language-pack-es-base', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-psb', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libdvdnav4', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-i810', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`sysklogd', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgpod3-nogtk', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`wireless-tools', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libqt4-core', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libtag1c2a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cryptsetup', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libvorbis0a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcucul0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgphoto2-2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kdeadmin-kfile-plugins', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`akregator', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libdns35', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`apache2.2-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-imaging', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libdns32', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`unzip', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`zlib1g-dev', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kde-style-polyester', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv-theme-blootube', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`amarok', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libavahi-client3', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kubuntu-docs', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`nvidia-glx-new', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libpolkit2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`bogofilter-bdb', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`gconf2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mime-support', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`alsa-base', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`rdiff-backup', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxine1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`zenity', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`sysvutils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`hplip-data', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`upstart-compat-sysv', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libkipi0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxine1-x', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libclucene0ldbl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libvolume-id0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`katapult', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xml-core', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cron', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`liblame-dev', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`bluez-utils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kubuntu-artwork-usplash', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgnome-keyring0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-input-all', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgcj-bc', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgcj8-jar', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`fontconfig-config', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libedit2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ttf-dejavu', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxtst6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgnome2-0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcdparanoia0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`linux-headers-2.6.24-19', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`nano', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`karm', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`inputattach', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kmplayer-konq-plugins', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`aspell', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libnspr4-0d', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`acpi-support', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-input-mouse', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`fuse-utils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-base-core', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libice6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`hplip-gui', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`scim-qtimm', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-libxml2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`networkstatus', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`nvidia-kernel-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`pppoeconf', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-apt', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`crimson', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ksvg', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libfaac0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxcb-shape0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcupsys2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libx11-data', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`time', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`linux-headers-generic', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cupsys', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv-theme-iulius', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libselinux1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libopenobex1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openssh-client', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-hyphenation-en-us', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`vbetool', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libplrpc-perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`belocs-locales-bin', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ntpdate', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`laptop-mode-tools', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libaa1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libc6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kwalletmanager', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgnustep-base1.14', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-nv', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libsm6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`w3m', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`klogd', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`dhcp3-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`vlc', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-kde', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mplayer', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`language-selector-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`wvdial', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`foomatic-db', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxxf86vm1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libaccess-bridge-java', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libpng12-0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libparted1.7-1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-via', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libconsole', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`wspanish', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`apt-utils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-geode', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcommons-net-java', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`udev', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libapm1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`linux-image-2.6.24-18-generic', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`defoma', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libpam-foreground', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmpeg2-4', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-writer', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libpixman-1-0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxcb-xv0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libsmokeqt1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv-backend', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kde-guidance-powermanager', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`iptables', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libsdl-pango1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`bash', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`make', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`util-linux', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libkrb53', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libiso9660-5', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxcursor1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libid3-3.8.3c2a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libdvbpsi4', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xfonts-utils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-input-kbd', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmeanwhile1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmusicbrainz4c2a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libksieve0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv-theme-blootubelite-wide', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`powernowd', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`avahi-daemon', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`lame', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`thunderbird-locale-es-ar', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgii1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`reiserfsprogs', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libneon26', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libneon27', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-uno', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ubuntu-minimal', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`popularity-contest', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`apparmor', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kmilo', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmad0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`hplip', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libfontenc1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libisccfg30', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libopencdk10', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cpio', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`powermgmt-base', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libstdc++6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`x11-xfs-utils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-i740', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`gnupg-agent', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`zip', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`apport', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libscrollkeeper0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`iputils-arping', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libhtml-tagset-perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`k3b', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`desktop-effects-kde', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ca-certificates', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`update-notifier-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`strace', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`vim-tiny', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcdio7', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`transcode', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mysql-server', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`fortunes-min', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-ati', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`liblwres30', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-siliconmotion', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`binutils', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`cdparanoia', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libfaad0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`foomatic-db-hpijs', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-gconf', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`openoffice.org-l10n-es', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libggi2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`less', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mysql-client-5.0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgphoto2-port0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxml-libxml-common-perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgomp1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ksnapshot', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`wodim', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`xserver-xorg-video-tseng', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libtext-charwidth-perl', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxt6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libmodplug0c2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`readline-common', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`linux-sound-base', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`ttf-opensymbol', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcap1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libwpd8c2a', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libapr1', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`usplash', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`mythtv-theme-titivillus-osd', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libid3tag0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libcupsimage2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libgnutls13', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libwrap0', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`kdebluetooth', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`netcat', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`lsof', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`python-pysqlite2', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

dpkg: aviso importante: falta el fichero de lista de ficheros del paquete
`libxau6', se supondrá que el paquete no tiene ningún fichero
actualmente instalado.

7249 ficheros y directorios instalados actualmente.)
Preparando para reemplazar libapache2-mod-php5 5.2.4-2ubuntu5.3 (usando libapache2-mod-php5_5.2.4-2ubuntu5.3_i386.deb) ...
Desempaquetando el reemplazo de libapache2-mod-php5 ...
Configurando libapache2-mod-php5 (5.2.4-2ubuntu5.3) ...
dpkg: error al procesar libapache2-mod-php5 (--install):
 el subproceso post-installation script devolvió el código de salida de error 10
Se encontraron errores al procesar:
 libapache2-mod-php5

---

### Post by badgandalf on 2008-08-03
Ok. I will reinstall kubuntu...
Thnx everyone who tried to help me here.

---

### Post by falkTX on 2008-08-03
I think I know what the problem was.
Did you installed through gdebi or dpkg any unnofficial deb?

My theory is that the deb you used (if you used any) was currupted, resulting into caos...

If that's the case please tells us so we can fix it

---

### Post by badgandalf on 2008-08-04
Last thing I tried to install was Ultrastar de Luxe ([www.ultrastardeluxe.org/](www.ultrastardeluxe.org/)). And you're probably right that all my problems started right then...

Rgds,

Ignacio

---

