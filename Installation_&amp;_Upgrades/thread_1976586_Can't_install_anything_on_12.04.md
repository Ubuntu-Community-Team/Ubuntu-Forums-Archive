---
title: "Can't install anything on 12.04"
date: 2012-05-08
forum: Installation &amp; Upgrades
---

### Post by Redfox814 on 2012-05-08
I just got ubuntu 12.04 and it was allowing me to install stuff until like 2 days ago. Can somebody help me? 

The error message:

Package operation failed
The installation or removal of a software package failed.

Details:
installArchives() failed: dpkg: error: parsing file '/var/lib/dpkg/status' near line 30836 package 'libpng12-0':
 field name `Depends2' must be followed by colon
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (2)
dpkg: error: parsing file '/var/lib/dpkg/status' near line 30836 package 'libpng12-0':
 field name `Depends2' must be followed by colon



Oh and I'm not that smart so keep it simple :D
Thanks!

---

### Post by mörgæs on 2012-05-09
Please boot the computer and run 

```
sudo apt-get update
sudo apt-get upgrade
```

Do you get other error messages doing so?

---

### Post by LRBA1 on 2012-05-27
I think I'm having the same problem when trying to update. After a time using ubuntu 12.04, Update-manager shows this error:

installArchives() failed:  Extrayendo plantillas para los paquetes: 47%% Extrayendo plantillas para los paquetes: 95%% Extrayendo plantillas para los paquetes: 100%% 
Preconfigurando paquetes ... 
 Extrayendo plantillas para los paquetes: 47%% Extrayendo plantillas para los paquetes: 95%% Extrayendo plantillas para los paquetes: 100%% 
Preconfigurando paquetes ... 
 Extrayendo plantillas para los paquetes: 47%% Extrayendo plantillas para los paquetes: 95%% Extrayendo plantillas para los paquetes: 100%% 
Preconfigurando paquetes ... 
 Extrayendo plantillas para los paquetes: 47%% Extrayendo plantillas para los paquetes: 95%% Extrayendo plantillas para los paquetes: 100%% 
Preconfigurando paquetes ... 
dpkg: error: parsing file '/var/lib/dpkg/available' near line 0: 
 field name `../../../../../share/pyshared/softwareproperties/gtk/utils.py' must be followed by colon 
Error in function:  

Now I can't update my system or install anything. It's a fresh  installation and everything I've install came from the repositories. Sudo apt-get update works as usual, but sudo apt-get upgrade says this:

Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Se actualizarán los siguientes paquetes:
  at-spi2-core gdb gir1.2-atspi-2.0 gir1.2-unity-5.0 gnome-control-center
  gnome-control-center-data gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter indicator-sound libasound2
  libatspi2.0-0 libgnome-control-center1 libgwibber-gtk2 libgwibber2
  libnautilus-extension1a libnux-2.0-0 libnux-2.0-common libsasl2-2
  libsasl2-modules libsnmp-base libsnmp15 libssl1.0.0 libunity9
  libutouch-geis1 libxml2 libzeitgeist-1.0-1 linux-headers-3.2.0-24
  linux-headers-3.2.0-24-generic-pae linux-image-3.2.0-24-generic-pae
  linux-libc-dev nautilus nautilus-data nux-tools openssl python-gi
  python-gi-cairo python-gobject python-libxml2 python-ubuntu-sso-client
  python-zeitgeist resolvconf software-center sudo ubuntu-docs
  ubuntu-sso-client ubuntu-sso-client-gtk ubuntu-sso-client-qt unity-greeter
  update-manager update-manager-core vim-common vim-tiny vino xserver-common
  xserver-xorg-core xserver-xorg-input-synaptics zeitgeist zeitgeist-core
  zenity zenity-common
63 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
Se necesita descargar 0 B/69,4 MB de archivos.
Se utilizarán 2.017 kB de espacio de disco adicional después de esta operación.
¿Desea continuar [S/n]? S
Extrayendo plantillas para los paquetes: 100%
Preconfigurando paquetes ...
dpkg: error: analizando archivo «/var/lib/dpkg/available» cerca de la línea 0:
 el nombre del campo `../../../../../share/pyshared/softwareproperties/gtk/utils.py' debe estar seguido por dos puntos
E: Sub-process /usr/bin/dpkg returned an error code (2)

¿Any idea? Thank you.

EDIT: I found this => [http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed](http://askubuntu.com/questions/98157/getting-error-message-package-operation-failed)
It solved my problem, hope it helps.
Thank you very much Florian Diesch from askubuntu.com

---

### Post by VMC on 2012-05-27
Try sudo ```
sudo apt-get -f install
``` to see if any errors are printed.

---

### Post by brevardo on 2012-10-15
I tried that and he's what I get:
e following packages have unmet dependencies:
 ubuntu-sso-client-gtk : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
                         Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
                        Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
rich@rich-Latitude-D620:~$ 
What can I try next?

---

### Post by mörgæs on 2012-10-17
> **brevardo said:**
> I tried that and he's what I get:
e following packages have unmet dependencies:
 ubuntu-sso-client-gtk : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
                         Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
 ubuntu-sso-client-qt : Depends: python-ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
                        Depends: ubuntu-sso-client (= 3.0.2-0ubuntu1) but 3.0.2-0ubuntu3 is installed
E: Unmet dependencies. **Try using -f**.
rich@rich-Latitude-D620:~$ 
What can I try next?

This.

---

### Post by brevardo on 2012-10-18
I've atually tried this too several times and here's what I get ( unless I'm not doing it properly ) 
rich@rich-Latitude-D620:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  ubuntu-sso-client-gtk ubuntu-sso-client-qt
The following packages will be upgraded:
  ubuntu-sso-client-gtk ubuntu-sso-client-qt
2 upgraded, 0 newly installed, 0 to remove and 62 not upgraded.
3 not fully installed or removed.
Need to get 0 B/569 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of ubuntu-sso-client-gtk:
 ubuntu-sso-client-gtk depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of python-ubuntu-sso-client on system is 3.0.2-0ubuntu3.
 ubuntu-sso-client-gtk depends on ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of ubuntu-sso-client on system is 3.0.2-0ubuntu3.
dpkg: error processing ubuntu-sso-client-gtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of software-center:
 software-center depends on ubuntu-sso-client-gtk; however:
  Package ubuntu-sso-client-gtk is not configured yet.
dpkg: error processing software-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-sso-client-qt:
 ubuntu-sso-client-qt depends on python-ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of python-ubuntu-sso-client on system is 3.0.2-0ubuntu3.
 ubuntu-sso-client-qt depends on ubuntu-sso-client (= 3.0.2-0ubuntu1); however:
  Version of ubuntu-sso-client on system is 3.0.2-0ubuntu3.
dpkg: error processing ubuntu-sso-client-qt (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 ubuntu-sso-client-gtk
 software-center
 ubuntu-sso-client-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
rich@rich-Latitude-D620:~$

---

### Post by mörgæs on 2012-10-19
Have you tried 

```
sudo dpkg --configure -a
```

?

---

