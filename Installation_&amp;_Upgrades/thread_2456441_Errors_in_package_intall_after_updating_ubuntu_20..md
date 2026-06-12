---
title: "Errors in package intall after updating ubuntu 20.04 to latest updates"
date: 2021-01-11
forum: Installation &amp; Upgrades
---

### Post by Manucho on 2021-01-11
Hello dear ubuntu users.

I had a working installation of ubuntu 20.04, since mid year 2020
Some days ago y updated as the software update asked for this.

The update worked fine, except after the update i could not install packages, or update them.
I took the fast solution, did a backup of the user files, and reinstalled ubuntu 20.04
I guessed, that rolling the updates right after the update wont mess the installlation.

However, the same error shows when attempting to install any aplication.

Ive tried to install with with -f modifier without luck

Ive seen solutions online, related to root access to the install files.

I think that the fresh install should not have any of this errors.

I appreciate to anyone who can help me with this.
Thanks in advance.

I let the example of what happens when trying to install virtualbox



[HTML]sudo apt-get install virtualbox
[sudo] contraseña para manuel: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
virtualbox ya está en su versión más reciente (6.1.10-dfsg-1~ubuntu1.20.04.1).
Los paquetes indicados a continuación se instalaron de forma automática y ya no son necesarios.
  libfprint-2-tod1 libllvm10
Utilice «sudo apt autoremove» para eliminarlos.
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 0 no actualizados.
3 no instalados del todo o eliminados.
Se utilizarán 0 B de espacio de disco adicional después de esta operación.
¿Desea continuar? [S/n] s
Configurando virtualbox-dkms (6.1.10-dfsg-1~ubuntu1.20.04.1) ...
Removing old virtualbox-6.1.10 DKMS files...

------------------------------
Deleting module version: 6.1.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-6.1.10 DKMS files...
Building for 5.8.0-36-generic
Building initial module for 5.8.0-36-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/virtualbox-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.8.0-36-generic (x86_64)
Consult /var/lib/dkms/virtualbox/6.1.10/build/make.log for more information.
dpkg: error al procesar el paquete virtualbox-dkms (--configure):
 el subproceso instalado paquete virtualbox-dkms script post-installation devolvió el código de salida de error 10
dpkg: problemas de dependencias impiden la configuración de virtualbox:
 virtualbox depende de virtualbox-dkms (>= 6.1.10-dfsg-1~ubuntu1.20.04.1) | virtualbox-source (>= 6.1.10-dfsg-1~ubuntu1.20.04.1) | virtualbox-modules; sin embargo:
 El paquete `virtualbox-dkms' no está configurado todavía.
  El paquete `virtualbox-source' no está instalado.
  El paquete `virtualbox-modules' no está instalado.
  El paquete `virtualbox-dkms' que provee `virtualbox-modules' aún no está configurado.

dpkg: error al procesar el paquete virtualbox (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de virtualbox-qt:
 virtualbox-qt depende de virtualbox (= 6.1.10-dfsg-1~ubuntu1.20.04.1); sin embargo:
 El paquete `virtualbox' no está configurado todavía.

dpkg: error al procesar el paquete virtualbox-qt (--configure):
 problemas de dependencias - se deja sin configurar
No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
                                           No se escribió un informe «apport» porque el mensaje de error indica que es un mensaje de error asociado a un fallo previo.
      Se encontraron errores al procesar:
 virtualbox-dkms
 virtualbox
 virtualbox-qt
E: Sub-process /usr/bin/dpkg returned an error code (1)
[/HTML]

---

### Post by maximiano on 2021-01-12
Hi,
I removed Virtualbox
sudo apt-get remove --purge virtualbox virtualbox-dkms virtualbox-source virtualbox-modules virtualbox-dkms

I installed python (is required for VBox 6.1_6.1.16)
sudo apt-get install python

i downloaded and installed VBox
wget [https://download.virtualbox.org/virtualbox/6.1.16/virtualbox-6.1_6.1.16-140961~Ubuntu~eoan_amd64.deb](https://download.virtualbox.org/virtualbox/6.1.16/virtualbox-6.1_6.1.16-140961~Ubuntu~eoan_amd64.deb)
sudo dpkg -i virtualbox-6.1_6.1.16-140961~Ubuntu~eoan_amd64.deb

then I runed VirtualBox and all my virtual machinnes operate equal before the error

good luck

---

### Post by Manucho on 2021-01-13
It worked, thanks!

---

