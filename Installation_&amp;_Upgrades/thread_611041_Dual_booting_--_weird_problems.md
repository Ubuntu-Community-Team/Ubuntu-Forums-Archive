---
title: "Dual booting -- weird problems"
date: 2007-11-12
forum: Installation &amp; Upgrades
---

### Post by cyph3x on 2007-11-12
I have ubuntu installed. i setup a partition editor (GParted) made 35gb of my hard drive unpartitioned, installed xp on the unpartitioned space and now i cant choose which OS to boot to. -- in drive manager in XP i cant mark the partition as active. (crap.) when i go into grub using a terminal off of a live cd and type 

```
find boot/grub/stage1
```

it says not found 

ack help i really dont want to have to reformat my ubuntu partition because i just got it the way i want. damn.

---

### Post by Pumalite on 2007-11-12
Boot off Live CD, mount partitions, post from Terminal:

sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by cyph3x on 2007-11-12
im not sure exactly how to do that... im fairly new to linux- but my terminal results for the commands you gave me are:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders, total 195371568 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49d78cdf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          273105   117676124    58701510   83  Linux
Partition 1 does not end on cylinder boundary.
/dev/sda2   *   117678960   189347759    35834400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3       189358155   195366464     3004155    f  W95 Ext'd (LBA)
Partition 3 does not end on cylinder boundary.
/dev/sda5       189358218   195366464     3004123+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory

```

thanks for the speedy reply

---

### Post by Pumalite on 2007-11-12
You didn't mount the partition, therefore menu.lst not found. Get Knoppix Live CD (mounts drives/partitions automatically at boot): [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
You seem to have a 2nd problem. Did you install XP after Ubuntu?

---

### Post by cyph3x on 2007-11-12
ok im DLing knoppix now... i did install XP after ubuntu. -- once i load knoppix what should i do?

---

### Post by Pumalite on 2007-11-12
At the Terminal(from the right partition)
cat /boot/grub/menu.lst

---

