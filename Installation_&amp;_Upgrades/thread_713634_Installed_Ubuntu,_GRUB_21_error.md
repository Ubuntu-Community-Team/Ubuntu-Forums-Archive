---
title: "Installed Ubuntu, GRUB 21 error"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by neodoxa on 2008-03-02
Hello...  I'm 100% new to linux.

I have tried installing Ubuntu 7.10 on a reformatted hard drive, it said the installation was successful, but when I boot up, it shows "Loading Stage 1.5  Grub 21 Error."

I read about some possible fixes, but havent been able to really fix anything since I'm new to linux.  It's the only OS on my system right now after reformatting.

Anyways...  I need help pretty badly, it is frustrating me.  Thanks in advance!

-neodoxa

P.S.  Here is the result of sudo fdisk -l :
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03da03da

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        8808    70750228+   7  HPFS/NTFS
/dev/sda2           28890       30401    12145140    5  Extended
/dev/sda3   *        8809       28889   161300632+  83  Linux
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris
/dev/sda6           28890       29645     6072507   82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

I tried using the Partition utility in the installer to create a 33/66% ratio of space on my HD for future installation of Windows XP.

If there is any other information I can provide, let me know.  Thanks again!

---

### Post by neodoxa on 2008-03-03
Sorry for the bump, I'm a student and need my computer as soon as possible.  I tried installing ubuntu twice, and reformatted in between.  I'm lost and have no idea how to fix this.  If anyone helps me, I will give you 10,000 cookies!  Home-made!

---

### Post by Josh1 on 2008-03-03
21 : Selected disk does not exist. This error is returned if the device part of a device- or full file name refers to a disk or BIOS device that is not present or not recognized by the BIOS in the system. 

[http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/](http://www.pendrivelinux.com/2007/08/11/grub-error-21-after-full-install-to-usb-hard-drive/)
[http://www.mepis.org/node/7330](http://www.mepis.org/node/7330)

Lots of different reasons why this could be happening.

---

### Post by zxscooby on 2008-03-03
That error indicates that a drive that is listed does not exist , or is not recognized by the bios.

Check your bios to see if the hard drive is detected properly, you could also try using the super grub disk to reinstall grub.  [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

check out this site [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
everything you wanted to know about grub but were afraid to ask.

---

### Post by neodoxa on 2008-03-03
Ok, well I fixed the problem by, believe it or not, switching the cable from the hard drive to the motherboard to another port.  That's it.  Haha.

Thanks for the help, guys. :popcorn:

---

### Post by zxscooby on 2008-03-04
SOOO.... um  When do my cookies arrive? :)

---

### Post by skozzy on 2008-03-04
I also had the same error when installing after many tries. I unplugged every drive except for the main drive (which is in IDE0 Master and it installed. If I replug all the drives the error came back, so I used the single drive for the install, then run all the latest updates, after that I was able to plug in the other drives. I think it's a Serial ATA problem for me.

---

### Post by Anubisxian on 2008-03-04
> **skozzy said:**
> I also had the same error when installing after many tries. I unplugged every drive except for the main drive (which is in IDE0 Master and it installed. If I replug all the drives the error came back, so I used the single drive for the install, then run all the latest updates, after that I was able to plug in the other drives. I think it's a Serial ATA problem for me.

Please bear in mind that I'm a total newb to Ubuntu, and I'm going through my own installation tribulation, but from what I've read, when you physically disconnect drives, then reconnect them, your PC will reassign the drive ID's, hd0, hd1, etc... Because of that, the menu file that Grub creates now may reference the wrong hard drive ID. I think you'd have to go into menu.lst and edit the drive IDs there.

I had the same problem: I physically disconnected my primary SATA drive to install Ubuntu on a separate IDE drive to keep my XP install kosher, then when I reconnected the SATA, I got the "error 21" message. I had other issues, mind you (hardware & BIOS related) and my install of Grub got hosed totally. I'm working on that now.

---

