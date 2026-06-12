---
title: "GRUB, Error 22, no such partition"
date: 2008-10-01
forum: Installation &amp; Upgrades
---

### Post by No.name.is.left on 2008-10-01
Hello, 

My first posting in this Forum so: "Hello everyone ;)" English is not my mother language so excuse my bad orthography and the wrong usage of some words, getting them from [www.dict.cc](www.dict.cc).

So my problem: installed Ubuntu-8.0.4 (sdb5) next to my Windows-partition (sdb1) after that GRUB didn't worked so I installed it manually with a LiveCD. When I'm choosing Ubuntu or Windows XP from the menu, I get the error 22. No such partiton. I checked my device.map:

> (hd0)	/dev/sda
(hd1)	/dev/sdb

and menu.lst:

> 
title		Ubuntu 8.04.1, kernel 2.6.24-19-generic
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=768080ca-eb63-4b83-aaa0-5a7f04415cd4 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root		(hd1,4)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=768080ca-eb63-4b83-aaa0-5a7f04415cd4 ro single
initrd		/boot/initrd.img-2.6.24-19-generic

title		Ubuntu 8.04.1, memtest86+
root		(hd1,4)
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows XP Professional
rootnoverify		(hd1,0)
savedefault
makeactive
chainloader	+1



As far as I see, it looks good. sdb5 gets to hd(1,4) in GRUB. The Kernel files exists in the directory's.

The fdisk answere of sudo fdisk -l:

> Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Disk identifier: 0xeb1580e8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *           1       15057   120945321    7  HPFS/NTFS
/dev/sdb2           15058       30401   123250680    5  Erweiterte
/dev/sdb5           15058       29772   118198206   83  Linux
/dev/sdb6           29773       30401     5052411   82  Linux Swap / Solaris



After 1 hour sitting, googling and thinking, I decided to post this text, looking forward to get some help with my problem.

-No.name.is.left,
stupid name but there was no other one, that i liked left.

---

### Post by knattlhuber on 2008-10-01
GRUB follows the boot order with the HD numbering. According to your menu.lst, your drive to boot Win and Ubuntu is hd(1,x) with x being the consecutive partition number.
But if that is your boot drive it is probably hd(0,x) in GRUB's book. Is it possible that there is a second HD which GRUB erroneously considers as hd(1,x)? Did you physically swap drives?

---

### Post by Pumalite on 2008-10-01
What do you have in sda. Grub's stage 1 might be in sda. Post:
sudo fdisk -lu
You might try changing the boot order in BIOS

---

### Post by No.name.is.left on 2008-10-02
> ubuntu@ubuntu:~$ sudo fdisk -lu

Platte /dev/sda: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xeb1580f3

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda4   *           0           0           0    0  Leer
Partition 4 endet nicht an einer Zylindergrenze.

Platte /dev/sdb: 250.0 GByte, 250059350016 Byte
255 Köpfe, 63 Sektoren/Spuren, 30401 Zylinder, zusammen 488397168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Disk identifier: 0xeb1580e8

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *          63   241890704   120945321    7  HPFS/NTFS
/dev/sdb2       241890705   488392064   123250680    5  Erweiterte
/dev/sdb5       241890768   478287179   118198206   83  Linux
/dev/sdb6       478287243   488392064     5052411   82  Linux Swap / Solaris
ubuntu@ubuntu:~$ 

I will try to change them, but normaly the sda should be empty atm, I wanted to use it as storage for music, photos and videos. Windows wanted the second HD as C:.

> Is it possible that there is a second HD which GRUB erroneously considers as hd(1,x)? 

There are 2 HDD's sda & sdb, sda should be empty and in sdb schould be Windows (NTFS) Ubuntu (Linux), the Ubuntu Swap (Linux Swap/Solaris) and Erweiterte, (don't know what this is, Erweiterte means in english: advanced).

In sda shouldn't be anything, there is partition sda4, but that partiton looks empty. I wasn't able to mount it and fdisk -lu shows that its empty to (leer=empty)


/
Booted Ubuntu. :-) 

Just changed it in (hd2, 4) after seeing that find /boot/grub/menu.lst answeres: (hd 0,4) and (hd 2,4). Don't really know why GRUB thinks sdb is hd2 but I will try to figure it out, it would be nice to get an explanation for that. Could it be, that update-grub fixed the device.map and changed there an entry, after that in the menu.lst and a simple grub-install /dev/sdb would fix the problem?

---

### Post by Pumalite on 2008-10-02
Grub tries to boot IDE even if it's installed in SATA:
[http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

---

### Post by caljohnsmith on 2008-10-02
No.name.is.left, try this to give us some clues how Grub might be seeing an (hd2) drive:
```
sudo grub
grub> find /boot/grub/stage1
```
Confirm that the find command again returns (hd0,4) and (hd2,4), and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
```
Please post the results of the above commands.

---

### Post by No.name.is.left on 2008-10-02
Now I'm just getting 
> grub> find /boot/grub/stage1
 (hd1,4)

grub> geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda

grub> geometry (hd1)
drive 0x81: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

grub> geometry (hd2)

Error 21: Selected disk does not exist


grub> 


Thats a bit confusing, because I edited the menu.lst and changed the entrys from (hd1,4) to (hd2,4) and it is working.

---

### Post by caljohnsmith on 2008-10-02
Are you sure you can still boot into Ubuntu OK? I don't see how using (hd2,4) could still be working if Grub can't even find a third drive. How about the next time you boot up and get the Grub menu, press "c" to get the Grub prompt, and do exactly the same thing:
```
grub> find /boot/grub/stage1
grub> geometry (hd0)
grub> geometry (hd1)
grub> geometry (hd2)
```
Note that when doing those commands from the Grub CLI at start up, it is not the same as doing them from within Ubuntu, because when you do them on start up your drives (hdX) are ordered according to the BIOS boot order; whereas when you are in Ubuntu, Grub's drives (hdX) correspond to the device order in Ubuntu's /dev directory so that:
```
(hd0) = sda
(hd1) = sdb
(hd2) = sdc
...etc.

```
So doing those Grub commands on start up should hopefully shed some light on what is going on with your setup. :)

---

