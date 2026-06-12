---
title: "hard drive config question"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by demopolis on 2008-07-19
Hello,

I just upgraded from Gutsy to Hefty today after my Gutsy install crashed for some unknown reason. Upon install I went with all the defaults as far as the partitions go. This was the result:


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19080   153260068+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6ede6ede

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9751    78324876   83  Linux
/dev/sdb2            9752       19457    77963445    5  Extended
/dev/sdb5            9752       19079    74927128+  83  Linux
/dev/sdb6           19080       19457     3036253+  82  Linux swap / Solaris


Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb5              71G  8.5G   59G  13% /
varrun                506M  680K  505M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   56K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
monroeja@loris:/mnt$


I have no idea how to interpret this info after doing some research. Are both my hard drives properly mounted? It appears to me that the sda drive still has the old Gutsy OS on it and Hefty simply installed onto sdb?

Can someone please help me to determine if my disks are mounted and ready to go. I can supply additional info if what I provided is not adequate.

Thanks

---

### Post by Pumalite on 2008-07-19
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
Post:
cat /media/sdb1/boot/grub/menu.lst

---

### Post by demopolis on 2008-07-20
Thanks. This is the result:

cat: /media/sdb1/boot/grub/menu.lst: No such file or directory

Bad install?

---

### Post by demopolis on 2008-07-23
Can anyone help? I'm not sure what to make of those results. Thanks.

---

