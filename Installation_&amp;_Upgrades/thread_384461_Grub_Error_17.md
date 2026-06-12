---
title: "Grub Error 17"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by pradeepadapa on 2007-03-14
hello guys,


             i am an user of UBUNTU, recently i hav updated to UBUNTU 6.10 nd i hav installed dual OS (UBUNTU nd WIN XP), the problem is the GRUB initialises fine but i m able to boot only into WIN XP but not UBUNTU, when i clink on UBUNTU kernel 2.6.17 i get an error screen where the error is like this


[SIZE="5"]cannot mount the partition
                GRUB error 17[/SIZE] 

i hav seen many posts considering this GRUB error17 but there wasnt mentioned anything about how to mount the ubuntu drive, when i try to recover the grub using the commands 

$sudo grub

grub>find /boot/grub/stage1
(hd0,5)
grub>root (hd0,5)

grub>setup (hd0)

it says that it has succeeded but when i restart again the same problem occurs, 

plse giv an solution to this problem, since i am able to LOGIN only to WINXP but not UBUNTU.

---

### Post by cyberdork33 on 2007-03-14
what is the partition layout for your machine?

On the grub menu, you can select an item and type 'e' to edit the entry. This will show you if it actually says (hdo,5) or not (if that is what it is supposed to say). Further, if it is incorrect, you can go to the broken line, hit 'e' again, and correct the line, then you can boot into the system. This editing is not saved though, so once you boot up you have to go into the system and fix the problem.

---

### Post by pradeepadapa on 2007-03-15
hi,

       when i edit the line using ' e ' i get that the line starting is (hd0,8) i change it to (hd0,5) and then boot, but still the same result " cannot mount the selected partition "

any ideas on hw to solve this problem

---

### Post by pradeepadapa on 2007-03-15
can anyone plse tell me how to sort this error of the GRUB

---

### Post by confused57 on 2007-03-15
Boot up the live cd, open a terminal  & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

If you can determine which is your Ubuntu root partition, you might want to check the contents of your /boot/grub/menu.lst:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

This "may" give a clue to what the problem is.

---

### Post by pradeepadapa on 2007-03-15
hello, when i edit the grub starting using ' e' nd then i boot into recovery mode after a min i m getting the folloutput,,,

/bin/sh : cant access tty;job control turned off

(initramfs) 

and the cursor stays there, it says to see help for options ,this initramfs has some commands just like when we type in the terminal

now how to correct this......

ya i'll post my fdisk -l list in a few min

---

### Post by pradeepadapa on 2007-03-15
my fdisk -l output is ----


Disk /dev/hdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hdc2            1276        9728    67898722+   f  W95 Ext'd (LBA)
/dev/hdc5            2551        5100    20482843+   7  HPFS/NTFS
/dev/hdc6            1276        2366     8763394+  83  Linux
/dev/hdc7            2367        2550     1477948+  82  Linux swap / Solaris
/dev/hdc8            5101        7650    20482843+   7  HPFS/NTFS
/dev/hdc9            7651        9728    16691503+   7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sda: 128 MB, 128974848 bytes
16 heads, 32 sectors/track, 492 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

---

### Post by confused57 on 2007-03-15
When you do the grub edit thing, pressing "e" & changing your root to (hd0,5), you might want to check the kernel line & make sure the root is correct there, root=/dev/hdc6....then press "b" to boot.

Did you happen to switch your hard drives around after installing Ubuntu?

---

### Post by cyberdork33 on 2007-03-15
is this the only hard drive? is there no hda?

---

### Post by pradeepadapa on 2007-03-15
hello confused in the kernel line i m having a line like root=/dev/hdc9........kernel version 

i will change the line to hdc6 nd see,

ya by changing (hd0,8 ) to hd0,5 by editing using 'e' and then booting also doesnt solve the problem.

ya this is only 1 hdd in which i hav installed both UBUNTU nd WIN XP........

---

### Post by cyberdork33 on 2007-03-15
/dev/hdc6 is the same as (hd0,5) for you... those things need to match on your root and kernel lines

---

### Post by pradeepadapa on 2007-03-15
ya got it guys, 

i changed the boot line to (hd0,5) and in the kernel line i changed it to /dev/hdc6 and it booted fine into UBUNTU,

then i edited the menu.lst file nd now my ubuntu sys is UP and RUNNING..........


[size=+4]**thanx guys for helping me**[/size]

---

### Post by cyberdork33 on 2007-03-16
glad to help!

---

