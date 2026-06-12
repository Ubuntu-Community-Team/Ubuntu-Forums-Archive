---
title: "This computer has no operating system"
date: 2010-07-30
forum: Installation &amp; Upgrades
---

### Post by Tony221268 on 2010-07-30
Using an nc10 samsung netbook with one HDD with existing XP install.  Installing using Ubuntu 10.0.4 Netbook iso, using method suggested below. I want to replace the XP entirely with Ubuntu for netbooks.

Used a non-media install using unetbootin as instructed here [https://help.ubuntu.com/community/Installation/FromWindow](https://help.ubuntu.com/community/Installation/FromWindow). Used unetbootin to create the usb (not a real usb although I have since done that with exactly the same result).

After successful boot into Ubuntu, I attempted to  do a proper"install" (i.e. move on from a "Try IT" USB version and overwrite the xp install) from within Ubuntu and when it gets to stage 4 I get the message: This computer has no operating systems on it.

In the case of using the unetbootin "virtual" usb it showed a partition of c. 7mb. In the case of the usb stick attempt it simply shows that usb stick as the partition. In the case of the real usb installing from boot option "Install to a Hard Disk" the same result. The HDD does not appear at stage 4 in any case. Choosing the advanced option at stage 4 gives an empty screen.

Using Gparted shows the HDD but the partition (in both cases USB and what I will call virtual USB) is locked and I cannot resize it.

---

### Post by P4man on 2010-07-30
If I understand it right, you put the ubuntu installation cd on the harddrive (or internal flash memory) and you are booting that to install ubuntu on to the same drive, right? I imagine thats only going to work (if at all) if you have prepared the partitions and you have a spare one (or spare drive) now to install ubuntu on to. I dont see how it can install to the one it just booted the live session from. 

Anyway I would just make live simple by booting from a real USB stick and use that to install from.

---

### Post by Tony221268 on 2010-07-30
Thanks but I don't think you read this:

Used unetbootin to create the usb (not a real usb although I have since done that with exactly the same result).

---

### Post by Tony221268 on 2010-07-30
Anyone got an answer???

---

### Post by roger_1960 on 2010-07-30
Hi

Not sure if this will help but....

If you boot to the Live "CD" (real usb) does the windows HDD/partition appear on the desktop or in file manager?  If so, right click on it and **_unmount_** it before clicking on the "install ubuntu" icon on the desktop.

---

### Post by Tony221268 on 2010-07-30
Below is not really a proper solution/ explanation for those without a USB but if someone reads this, this was my blundering effort. Point is, I know it worked at least. Note, I also had a spare PC to make my USB for the install stage (see below). No idea if the solution by Roger works but it sounds sensible, less effort and no USB required...thanks for that.
 
I downloaded the bootable Gparted [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) to the USB, made that bootable using Universal USB Installer. I then booted to that and deleted the XP partition. I added an ext partition and exited Gparted. To install, I then rebooted using the bootable USB (now with the original netbook.iso made using a spare pc), chose the new ext partition and install went OK...

---

