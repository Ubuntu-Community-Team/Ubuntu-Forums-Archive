---
title: "grub messed out, need to restore it!"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by mexlinux on 2008-07-29
Hi:
Something happen in my laptop (it's a Dell XPS M1330)
Only uncommon thing is that I click on the Media Direct button when it was power off.....

So ok next boot grub reported Error 17 and din't worked.

I went to a livecd (wifiway is the only one I had at that time)
I typed the grub commands:

#grub
>root (hd0,5)
>setup (hd0)
>quit

Now the PC boots, but into a ramdrive.... what the heck?

Then I got a Ubuntu Cd, and tried the method described here:
[http://ubuntuforums.org/archive/index.php/t-24113.html](http://ubuntuforums.org/archive/index.php/t-24113.html)

but whem I get to manual partition it says I only have sda device as the only available partition.... so I can not mount a thing.....

I tried to get a full backup of my home,,,, but there is no home!?!?!

I can see the disk is mounted in /media/disk
and there I can see a "home"
but says is a block device (1.7Gb)

what?!!!1




If I go again to grub from the ubuntu cd I get:
Error 21: Selected disk does not exist


Any clues?!

---

### Post by Pumalite on 2008-07-29
Post:
sudo fdisk -lu

---

### Post by spiderbatdad on 2008-07-29
As you go through the beginning stages of installation from the live cd, instead of partitioning, you should be offered the option to "fix grub."

---

### Post by mexlinux on 2008-07-29
> **Pumalite said:**
> Post:
sudo fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu
Atención: no se tienen en cuenta los datos adicionales de la tabla de particiones 7
Atención: no se tienen en cuenta los datos adicionales de la tabla de particiones 7
Atención: no se tienen en cuenta los datos adicionales de la tabla de particiones 7
Atención: el indicador 0x7965 inválido de la tabla de particiones 7 se corregirá mediante w(rite)

Disco /dev/sda: 160.0 GB, 160041885696 bytes
255 cabezas, 63 sectores/pista, 19457 cilindros, 312581808 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Identificador de disco: 0x18000000

Disposit. Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *   307337216   312578047     2620416    c  W95 FAT32 (LBA)
/dev/sda2          161792    21133311    10485760    7  HPFS/NTFS
/dev/sda3   *    21133312    80264171    29565430    7  HPFS/NTFS
/dev/sda4        80276866   312578047   116150591    f  W95 Ext'd (LBA)
/dev/sda5       307337216   312578047     2620416   dd  Desconocido
/dev/sda6        80276868   298021814   108872473+  83  Linux
/dev/sda7   ?   875026731  2794277194   959625232   6f  Desconocido

Las entradas de la tabla de particiones no están en el orden del disco

---

### Post by mexlinux on 2008-07-29
> **spiderbatdad said:**
> As you go through the beginning stages of installation from the live cd, instead of partitioning, you should be offered the option to "fix grub."

nope

---

### Post by Pumalite on 2008-07-29
You have a problem in sda5 and sda7.
Double check your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

---

### Post by mexlinux on 2008-07-29
> **Pumalite said:**
> You have a problem in sda5 and sda7.
Double check your drive with rescuecd:
[http://www.sysresccd.org/Download](http://www.sysresccd.org/Download)

I'll try to burn that.....
in the meantime any tool to check the drive that I can install via synaptic on my live cd ubuntu?

---

