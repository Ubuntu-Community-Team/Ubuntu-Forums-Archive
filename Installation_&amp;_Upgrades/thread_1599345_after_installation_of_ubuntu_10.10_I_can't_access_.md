---
title: "after installation of ubuntu 10.10 I can't access windows XP"
date: 2010-10-17
forum: Installation &amp; Upgrades
---

### Post by srdjan015 on 2010-10-17
hi, i'm beginner for linux.. soo :)

today i  installed ubuntu  like it says on  ubuntu home page, 

I installed it with Windows Xp, on the same partition with sharing it..

Everything ended well but after restarting, i didn't have option to go to windows..

Now system says that file system for ubuntu teaks whole hard disc..


How can i go to windows? I have installed  grub2 but even so, it doesn't give me an option to pick OS..

Thanks, and i hope to quick help :)

---

### Post by alexan on 2010-10-17
First.. let's see if you still have windows:

Application > Accessories > Terminal
[b]sudo fdisk -l[b]

---

### Post by srdjan015 on 2010-10-17
```
Disk /dev/sda: 4007 MB, 4007657472 bytes
43 heads, 43 sectors/track, 4233 cylinders
Units = cylinders of 1849 * 512 = 946688 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04030201

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4234     3913188    b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007a208

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60419   485314560   83  Linux
/dev/sdb2           60420       60802     3068929    5  Extended
/dev/sdb5           60420       60802     3068928   82  Linux swap / Solaris

```/edit : I don't understand this.. hard disk should have abut 500 Gb..

It seams like it is gone :)...

Now, i tried to reinstal(boot) windows back but it stops at rekognising my hardver components and does nothing...

How could i format hard disk and go back to Win

---

### Post by coffeecat on 2010-10-17
> **srdjan015 said:**
> I installed it with Windows Xp, on the same partition with sharing it..

No, sorry. Looking at your fdisk output, it looks as though you chose 'use whole disk' in the installer and the installer did just that. It used the whole disk for Ubuntu, wiping out Windows. There was another option you should have used - I can't remember what it is called, but it allows you to shrink  your Windows partition and install Ubuntu to the free space.

> **srdjan015 said:**
> How could i format hard disk and go back to Win

It depends. Did you make an image of your Windows install with something like Norton Ghost or Acronis? If so, you will have to use the Ubuntu live CD to re-format the HD again and create a NTFS partition for Acronis/Norton to restore the image to. If you can do that, someone can tell you how to use Gparted in the live CD to make a NTFS partition.

If you do not have an image, it means a fresh install, either with a Windows install CD or with OEM restore CDs that come with an OEM computer.

---

### Post by Rahul dev on 2010-10-17
hey you have installed your Ubuntu in full hard drive, without any specific partition for Linux. Now you should install Winxp  and make a partiotin for Ubuntu to install . Then install Ubuntu in this specified partition by using Wubi

---

### Post by garvinrick4 on 2010-10-17
If you want to go back to Windows just use the install disk and it will overwrite your Linux on your disk. You want Windows on your whole disk, it will do the rest.

---

### Post by srdjan015 on 2010-10-17
Back on windows :)

Thanks to all..

---

