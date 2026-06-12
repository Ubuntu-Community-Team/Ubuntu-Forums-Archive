---
title: "linux-image update broken"
date: 2007-09-01
forum: Installation &amp; Upgrades
---

### Post by Fenix-TX on 2007-09-01
I'm using Kubuntu Feisty Fawn.

I have an error upgrading today linux-imagen:

```
Configurando linux-image-2.6.20-16-generic (2.6.20-16.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.20-16.29 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.20-16.29 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.20-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2

```

If i exec apt-get -f install i get this message:
```

sudo apt-get -f install
Leyendo listas de paquetes... Hecho
Creando árbol de dependencias
Leyendo información de estado... Hecho
0 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.
1 no instalados del todo o eliminados.
Necesito descargar 0B de archivos.
Se utilizarán 0B de espacio de disco adicional después de desempaquetar.
Configurando linux-image-2.6.20-16-generic (2.6.20-16.31) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.20-16-generic
Not updating initrd symbolic links since we are being updated/reinstalled
(2.6.20-16.29 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled
(2.6.20-16.29 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
[: 25: ==: unexpected operator
exec: 25: -a: not found
User postinst hook script [/sbin/update-grub] exited with value 2
dpkg: error al procesar linux-image-2.6.20-16-generic (--configure):
 el subproceso post-installation script devolvió el código de salida de error 2
Se encontraron errores al procesar:
 linux-image-2.6.20-16-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Fenix-TX on 2007-09-01
Nobody has this problem with latest kernerl update?

---

### Post by Agrezar on 2007-09-01
I had a simular problem, I think it's due to the gfxmenu grub installled. I searched around abit and found that the /usr/sbin/udate-grub was an sh file, and is supposed to be a bash file. 

sudo  gedit /usr/sbin/update-grub

change the #!/bin/sh to #!/bin/bash

sudo apt-get dist-upgrade

should work now :D

---

### Post by Fenix-TX on 2007-09-01
Thanks, that works, but i had to edit /sbin/update-grub instead of /usr/sbin/update-grub but works now :)

---

### Post by Agrezar on 2007-09-01
np man glad to help :D

---

