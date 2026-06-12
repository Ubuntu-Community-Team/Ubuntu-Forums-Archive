---
title: "desktop consists wallpaper nothing else"
date: 2008-06-10
forum: Installation &amp; Upgrades
---

### Post by frost151n on 2008-06-10
hi, i seemed to have messed up my ubuntu somehow, so i am going to do what any selfrespecting lifetime windows user would do... uninstall and then reinstall!!!
problem is i dont know how to uninstall ubuntu!!!
can someone please help???

edit* i'm using an hp dv2700 with vista dual boot. i dont wanna touch the vista partition.

---

### Post by Pumalite on 2008-06-10
You can install on top of the old installation. Just go Manual and point to the right partitions. You can ignore /swap.

---

### Post by frost151n on 2008-06-10
eh?
im really sorry, but i've been using ubuntu for like a week!!!

---

### Post by Pumalite on 2008-06-10
Are you able to boot a Live CD?

---

### Post by frost151n on 2008-06-10
yes, i have 8.04.

---

### Post by Pumalite on 2008-06-10
Boot it. Go to the Terminal and post the output of:
sudo fdisk -lu
(Copy and paste here)

---

### Post by frost151n on 2008-06-10
ok,
i paste it tomorrow, my comps in the office

---

### Post by frost151n on 2008-06-11
Here...

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0bddba0e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   147379871    73689904+   7  HPFS/NTFS
/dev/sda2       147380310   305765144    79192417+  83  Linux
/dev/sda3       305765145   312576704     3405780    5  Extended
/dev/sda5       305765208   312576704     3405748+  82  Linux swap / Solaris

---

### Post by Pumalite on 2008-06-11
At the Terminal:
sudo mkdir /media/sda2
sudo mount -t ext3 /dev/sda2 /media/sda2
Post:
cat /media/sda2/boot/grub/menu.lst

---

