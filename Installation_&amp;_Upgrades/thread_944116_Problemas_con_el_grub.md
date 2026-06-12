---
title: "Problemas con el grub"
date: 2008-10-11
forum: Installation &amp; Upgrades
---

### Post by Sipna on 2008-10-11
Hola a todos soy super novato en linux, asi q paciencia si?

les cuento mi problema tengo 3 discos 2 de 40 Gb (IDE) y uno de 250 Gb (SATA)

En un disco de 40Gb tengo ubuntu (disco master IDE), en el otro de 40Gb (disco esclavo IDE) tengo Windows Xp y el de 250Gb es libre, para respaldo, las fotos musica etc

el puento es q el el grub no me da la opcion de de entrar a Xp, claro si booteo del disco esclavo si me entra, pero si booteo desde el maste pasa derecho a ubuntu 

usando el comando sudo fdisk -l me da esta informacion

Disco /dev/sda: 40.0 GB, 40020664320 bytes
255 cabezas, 63 sectores/pista, 4865 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x48a648a5

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *           1        4660    37431418+  83  Linux
/dev/sda2            4661        4865     1646662+   5  Extendida
/dev/sda5            4661        4865     1646631   82  Linux swap / Solaris

Disco /dev/sdb: 41.1 GB, 41110142976 bytes
255 cabezas, 63 sectores/pista, 4998 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0x1b501b4f

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdb1   *           1        4997    40138371    7  HPFS/NTFS

Disco /dev/sdc: 250.0 GB, 250059350016 bytes
255 cabezas, 63 sectores/pista, 30401 cilindros
Unidades = cilindros de 16065 * 512 = 8225280 bytes
Identificador de disco: 0xa353a353

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sdc1               1       30401   244196001    7  HPFS/NTFS

Usado en comando gedit /boot/grub/menu.lst me da esta informacion

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6102dcb6-cbb1-4c88-bf2e-3c8cae2d1e41 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=6102dcb6-cbb1-4c88-bf2e-3c8cae2d1e41 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet


Leyendo un poco en otros post se dice q agrege esta opcion al final 

title		Windows XP Professional SP2
root		(hd1,0)
savedefault
makeactive
chainloader	+1

Pero igual no entra se queda en Starting  y no entra guindows

alguien me puede explicar q hacer!!!

Gracias!!! (ojo soy novato):confused:

---

### Post by caljohnsmith on 2008-10-11
Por favor, use Inglés en este foro en el futuro, pero para resolver su problema, abra su menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
Y sustituir la entrada de Windows con ambos:
```
title	   Windows XP (hd1)
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1

title	   Windows XP (hd2)
root       (hd2,0)
map        (hd0) (hd2)
map        (hd2) (hd0)
chainloader +1
```
Reinicie (reboot) su equipo, y tratar cada una de esas entradas de Windows; uno debe trabajar. Permítame saber si usted tiene problemas. :)

---

### Post by AlexBellisBrown on 2008-10-11
Aunque parece dificil, no lo es. Pero si, en este foro tienes que hablar en ingés. Además, ¿Existe un foro en español para usuarios de Ubuntu? Acabo de mirar en Google, y me parece que no. Que raro...

---

### Post by Sipna on 2008-10-11
thanks!!!! is working my two system!!! :lolflag:

---

