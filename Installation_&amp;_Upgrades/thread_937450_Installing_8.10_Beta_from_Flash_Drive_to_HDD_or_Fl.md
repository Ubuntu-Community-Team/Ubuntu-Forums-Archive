---
title: "Installing 8.10 Beta from Flash Drive to HDD or Flash Drive."
date: 2008-10-03
forum: Installation &amp; Upgrades
---

### Post by C.S.Cameron on 2008-10-03
I was getting tired of installing ubuntu using obsolete CD's.
I decided to give usb-creator a try.
Installed from here: 
[https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7](https://launchpad.net/ubuntu/intrepid/i386/usb-creator/0.1.7)
Downloaded 8.10 Beta iso to desktop.
Inserted 2 gig Flash drive
Launched usb creator.
After confirming drives and iso location a bootable, persistent image was created on the thumbdive.
Total time about two minutes.
From there I booted the new Flash Drive and decided to install Intrepid Beta to a second Flash Drive rather than to HDD.
(I had previously disabled the internal HDD's so as not to mess up the windows mba).
I ran install from the Flash created by usb-creator.
At partitioning I chose manual.
Left a partiton for fat 32 at the beginning so that I can copy files from a windows computer.
Created a home partition formatting to ReiserFS, (mount point /home), (Thanks Herman).
Created a root partition again formatting to ReiserFS, (mount point /).
Then created a swap partition just in case.
Install went well. Boot did not. Grub could not find the files.
Install seemed to get confused with which Flash Drive was which, (this should not happen installing to Hard Disk).
I edited /boot/grub/menu.lst, at the bottom, changed root to (hd0,2) as this is where my root partition ended up.
I am now busy building a new system on Pendrive.

---

### Post by uflieven on 2008-10-04
I have been able to make a live-USB system, but it takes a fairly long way (can post it if you really want it). However, I've never done it from one USB-key to another. I always copied some files from CD to my USB-key. It is also done using ext2 filesystem rather than ReiserFS.

I would not create a swap partition on the flash drive, it may prematurely age the drive.

---

### Post by C.S.Cameron on 2008-10-04
Difficult and lengthy persistent installs to pendrive are a thing of the past.
Usb-creator builds a Flash Drive similar to the Pendrivelinux one in about 2 minutes.
Installed on a 2G Thumb Drive, I end up with 1.2G free.
The drive is formatted in Fat32 and is still usable as a storage device in windows.
This is a Live USB similar to the Live CD, it can be used to install Ubuntu just like the CD.
I chose to install to another Pen Drive in this example rather than to hard drive.
This creates a working Flash Drive with all the features of a hard drive install, it can be highly customized.
I chose ReiserFS after a tip by Herman, you can use ext2 or ext3 formatting as you wish.
ReiserFS seems a bit faster when used on a Flash Drive.
On a decent computer, my swap is flatline. It only gets used when booting older, low RAM  machines.

---

### Post by msktje on 2008-10-05
i have a question about the persistent feature of the usb creator. Now i have a stick with a casper-rw partition where i have persistent of the whole system. If i install extra programs on the liveusbstick the next time i boot they are still installed. Is this with this persitent also the case or is it just a persistent home that is created?

---

### Post by C.S.Cameron on 2008-10-06
Usb-creator builds a casper-rw file.
Not sure yet if persistence is working

---

