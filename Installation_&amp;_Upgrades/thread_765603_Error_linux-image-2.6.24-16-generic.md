---
title: "Error linux-image-2.6.24-16-generic"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by mzdsb on 2008-04-24
After upgrading from gutsy via 'sudo update-manager -c -d' to hardy (yes, -d because it was a few hours before the oficial release, don't ask) i keep getting next error:

```

mz@gantz:~$ sudo apt-get dist-upgrade 
[sudo] password for mz: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Calculando la actualización... Listo
0 actualizados, 0 se instalarán, 0 para eliminar y 0 no actualizados.
5 no instalados del todo o eliminados.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
¿Desea continuar [S/n]? s
Configurando linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.24-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de linux-ubuntu-modules-2.6.24-16-generic:
 linux-ubuntu-modules-2.6.24-16-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-ubuntu-modules-2.6.24-16-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
 linux-image-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
 linux-image-generic depende de linux-ubuntu-modules-2.6.24-16-generic; sin embargo:
 El paquete `linux-ubuntu-modules-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-image-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-2.6.24-16-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-generic:
 linux-restricted-modules-generic depende de linux-restricted-modules-2.6.24-16-generic; sin embargo:
 El paquete `linux-restricted-modules-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-generic (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 linux-image-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-generic
 linux-image-generic
 linux-restricted-modules-2.6.24-16-generic
 linux-restricted-modules-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
mz@gantz:~$ 

``` 

it would be no big deal, but this errors keeps me from instaling the restricted modules, that means no 3d and what's even worse, 800x600 res.

anyone with the same problem? or even better... anyone with a solution??

thanks

---

### Post by Pumalite on 2008-04-24
Post the output of:
sudo dpkg --configure -a

---

### Post by mzdsb on 2008-04-24
> **Pumalite said:**
> Post the output of:
sudo dpkg --configure -a


here it goes:

```

mz@gantz:~$ sudo dpkg --configure -a
Configurando linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.24-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
dpkg: problemas de dependencias impiden la configuración de linux-ubuntu-modules-2.6.24-16-generic:
 linux-ubuntu-modules-2.6.24-16-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-ubuntu-modules-2.6.24-16-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-2.6.24-16-generic:
 linux-restricted-modules-2.6.24-16-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-2.6.24-16-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-image-generic:
 linux-image-generic depende de linux-image-2.6.24-16-generic; sin embargo:
 El paquete `linux-image-2.6.24-16-generic' no está configurado todavía.
 linux-image-generic depende de linux-ubuntu-modules-2.6.24-16-generic; sin embargo:
 El paquete `linux-ubuntu-modules-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-image-generic (--configure):
 problemas de dependencias - se deja sin configurar
dpkg: problemas de dependencias impiden la configuración de linux-restricted-modules-generic:
 linux-restricted-modules-generic depende de linux-restricted-modules-2.6.24-16-generic; sin embargo:
 El paquete `linux-restricted-modules-2.6.24-16-generic' no está configurado todavía.
dpkg: error al procesar linux-restricted-modules-generic (--configure):
 problemas de dependencias - se deja sin configurar
Se encontraron errores al procesar:
 linux-image-2.6.24-16-generic
 linux-ubuntu-modules-2.6.24-16-generic
 linux-restricted-modules-2.6.24-16-generic
 linux-image-generic
 linux-restricted-modules-generic
mz@gantz:~$

```

---

### Post by Pumalite on 2008-04-24
Run:
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by mzdsb on 2008-04-24
> **Pumalite said:**
> Run:
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

already tried that, still having dependency problems :(

i managed to get a clean 'sudo dpkg --configure -a' output after removing the packages that were giving me problems
```

sudo apt-get remove linux-image-2.6.24-16-generic
sudo apt-get remove linux-ubuntu-modules-2.6.24-16-generic
sudo apt-get remove linux-image-generic
sudo apt-get remove linux-restricted-modules-2.6.24-16-generic
sudo apt-get remove linux-restricted-modules-generic

``` (maybe not in that order, dunno if that was important)

But i still can't install the new kernel, same dependency problems:
```

mz@gantz:~$ sudo dpkg --configure -a
mz@gantz:~$ sudo aptitude install linux-image-2.6.24-16-generic
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Construir la base de datos de etiquetas... Hecho
Se instalarán los siguiente paquetes NUEVOS:
  linux-image-2.6.24-16-generic 
0 paquetes actualizados, 1 nuevos instalados, 0 para eliminar y 0 sin actualizar.
Necesito descargar 0B/18,4MB de ficheros. Después de desempaquetar se usarán 61,8MB.
Escribiendo información de estado extendido... Hecho
Seleccionando el paquete linux-image-2.6.24-16-generic previamente no seleccionado.
(Leyendo la base de datos ...  
287904 ficheros y directorios instalados actualmente.)
Desempaquetando linux-image-2.6.24-16-generic (de .../linux-image-2.6.24-16-generic_2.6.24-16.30_i386.deb) ...
Done.
Configurando linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.24-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.24-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
Un paquete no se pudo instalar. Intentado recuperarse:
Configurando linux-image-2.6.24-16-generic (2.6.24-16.30) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.24-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.24-16-generic
Leyendo lista de paquetes... Hecho                   
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Leyendo la información de estado extendido      
Inicializando el estado de los paquetes... Hecho
Escribiendo información de estado extendido... Hecho
Construir la base de datos de etiquetas... Hecho     
mz@gantz:~$

```

and (correct me if i'm wrong) i need the last kernel in order to install the restricted modules and get my 3d acceleration back.

---

### Post by mzdsb on 2008-04-24
First of all sorry for posting so quickily.

i think the problem lays in /sbin/update-grub
if i try to run the command, i get the same error that I get when I try to install a kernel:
```

mz@gantz:~$ /sbin/update-grub
[: 25: ==: unexpected operator
exec: 25: -a: not found
mz@gantz:~$

```

I'm posting my /sbin/update-grub, so you can tell me if yours look the same.
```

#!/bin/sh
#
# Wrapper to warn user about kernel-img.conf move
#

if grep -q '  */sbin/update-grub$' /etc/kernel-img.conf 2> /dev/null ; then
	cat <<EOF
Your /etc/kernel-img.conf needs upgrade. Read grub's NEWS.Debian[1]
file and follow its instructions.

 1. /usr/share/doc/grub-gfxboot/NEWS.Debian.gz


EOF
fi

if [ -x /usr/sbin/update-grub.real ]; then
	if [ "$0" == "/sbin/update-grub" ]; then
		echo "You shouldn't call /sbin/update-grub. Please call /usr/sbin/update-grub instead!"
		echo
	fi
	exec -a update-grub /usr/sbin/update-grub.real $*
else
	echo "Your /usr is broken, please fix it before call this wrapper!"
fi

```

NOTE: i'm using grub-gfxboot

---

### Post by Pumalite on 2008-04-24
Mine is the same.

---

### Post by mzdsb on 2008-04-24
Solved?
After realizing that it has something to do with grub-gfxboot I did a quick search on the forums and this is what i found:
[http://ubuntuforums.org/showthread.php?t=595008](http://ubuntuforums.org/showthread.php?t=595008)

it's in spanish, it says 'do a sudo dpkg-reconfigure dash and anwser NO'

well, that seems to solve my problems, i'll tell you after rebooting...

---

### Post by Pumalite on 2008-04-24
Parece que lo tienes resuelto.

---

### Post by mzdsb on 2008-04-24
> **Pumalite said:**
> Parece que lo tienes resuelto.

yes, solved :D

now i have no sound, but i think this is enough for this post, i sould open another about audio :p

I'll try to change the topic to [SOLVED]

thank you all for your help :)

---

sound problem solved with 'sudo /etc/init.d/udev restart'

---

### Post by Pumalite on 2008-04-24
Good luck.

---

