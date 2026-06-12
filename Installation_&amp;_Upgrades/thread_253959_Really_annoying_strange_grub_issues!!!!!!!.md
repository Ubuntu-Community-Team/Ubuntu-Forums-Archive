---
title: "Really annoying strange grub issues!!!!!!!"
date: 2006-09-09
forum: Installation &amp; Upgrades
---

### Post by mattpark on 2006-09-09
Having some very odd and annoying issues with my dual boot setup.

Ubuntu is intalled on sdd, and xp on sda. Ubuntu installer ran fine, nice and dandy. When i boot nothing works, and grub keeps bringing back error 17 on all options. 

Now, here is the odd thing, i managed to get ubuntu to boot by changing the grub line to "hd0" even though its sdd. 

sudo fdisk -l brings back:

> Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30400 244187968+ 7 HPFS/NTFS

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdb1 1 24321 195358401 7 HPFS/NTFS

Disk /dev/sdc: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 9725 78116031 7 HPFS/NTFS

Disk /dev/sdd: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot Start End Blocks Id System
/dev/sdd1 * 1 9557 76766571 83 Linux
/dev/sdd2 9558 9964 3269227+ 5 Extended
/dev/sdd5 9558 9964 3269196 82 Linux swap / Solaris


So i have ubuntu, ubuntu safe mode, and mem test working just fine. I;ve tried all i can to get XP working from grub again, but all i get is error 17! I've tried hd0, hd1, hd2, and hd3. And also partition 1 on all drives too! Can't work out whats going on, why is sdd hd0? Surely sda should be hd0? 

Is there an issue with sata drives or something? Really need to get xp booting again! Preferably on grub so i can dual boot, but if there is no other option i'll just fixmbr?:-# 

Help!

Matt

---

### Post by mattpark on 2006-09-09
Here is the content of menulst:

> ## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-amd64-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-amd64-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-26-amd64-generic root=/dev/sdd1 ro single
initrd          /boot/initrd.img-2.6.15-26-amd64-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd3,0)
savedefault
makeactive
chainloader     +1


---

### Post by mattpark on 2006-09-09
Here is device.map:

> (hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd



The odd thing is, i got ubuntu to work by changing the menu.lst for it to "hd0", which SHOULD be the XP drive!?

SO confused!

---

### Post by wieman01 on 2006-09-09
Can you add a screenshot of GParted, please? That would help quite a bit. :-)

---

### Post by whizbaby on 2006-09-09
Huh? So you mean when you exchange *root(hd3,0)* by *root(hd0,0)* in the windows entry (and vice versa in the ubuntu entries) nothing works at all, contrary to the device.map?

---

### Post by mattpark on 2006-09-09
There we go! I'll do windows drive too.. 1 sec

---

### Post by mattpark on 2006-09-09
and. windows drive...

---

### Post by mattpark on 2006-09-09
Just to clear up... I got Ubutu to work by changing it to hd0,0!

Windows - i can't get to work at all, no matter what i put in>!

---

### Post by confused57 on 2006-09-09
You could try a mapping command similar to this:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

---

