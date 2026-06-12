---
title: "Lucid on USB"
date: 2009-12-03
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by zwygart on 2009-12-03
Hi everybody,

I installed jaunty on flash drive, which worked well,
then with karmic it complains about /dev/sr0 not existing during boot. Even the lates does it. 
Then I had to reinstall jaunty, wich now doesn't work.
I tried out Lucid, it does same thing than karmic. It works under Virtualbox but on USB it will not found /dev/sr0. 

I wanted to edit the initrd.lz  During the unzip with 7z (as root) it exited because the partition was full. So here is the problem

The USB remounted as sdc but only my first 2 partitions
Data (12G)
jaunty (800M)
The third was gone.

I plugged out/in the key several time hopping this will help.
Looking under gparted the Flash drive was empty (No partitions)
Fdisk has this :
Les entrées de la table de partitions ne sont pas dans l'ordre du disque
AVERTISSEMENT: données surperflues ignorées dans la table de partition 6
AVERTISSEMENT: données surperflues ignorées dans la table de partition 6
AVERTISSEMENT: données surperflues ignorées dans la table de partition 6
AVERTISSEMENT: fanion 0x0030 non valide dans la table de partitions 6, sera corrigé par w(écriture)

Disque /dev/sdb: 16.1 Go, 16173236224 octets
64 têtes, 32 secteurs/piste, 15424 cylindres
Unités = cylindres de 2048 * 512 = 1048576 octets
Identifiant de disque : 0x00080570

Périphérique Amorce  Début        Fin      Blocs     Id  Système
/dev/sdb1               1       13633    13960176    b  W95 FAT32
/dev/sdb3           13634       15424     1833984    5  Etendue
/dev/sdb5           13634       14529      917488    b  W95 FAT32
/dev/sdb6   ?       16066       17602     1572888   30  Inconnu

blkid write :
/dev/sdb1: LABEL="Data" UUID="48CD-40AC" TYPE="vfat" 
/dev/sdb5: LABEL="jaunty" UUID="251B-D5E8" TYPE="vfat" 


I was able to mount the partition and copy the content, but I also have GRUB which I would preserve.

How to get the partitions back whitout formatting?

Question less important how to boot lucid on USB?
Usually I copy teh content off the ISO to a partition, then write the content of isolinux loader to my grub, essentially the kernel and initrd lines.

Thanks for help

---

### Post by Kilz on 2009-12-03
You are in the General area. This area is for released versions. Lucid is (just barley started) under development. [Go here ]("http://ubuntuforums.org/forumdisplay.php?f=310")and post and you might get an answer.

---

### Post by zwygart on 2009-12-03
I know,

but it was for my USB/partition problem essentially,

I deleted the partition sdb6 with fdisk, then it was partition sdb5 that has superfluous entry. I deleted sdb5, and the USB key went correct with my Data partition, mountable under windows and bootable.

Thanks for fast answer. 

I wrote this to help people hwo may have similar problem

---

