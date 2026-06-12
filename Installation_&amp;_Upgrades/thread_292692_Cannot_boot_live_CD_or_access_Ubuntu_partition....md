---
title: "Cannot boot live CD or access Ubuntu partition..."
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by Stonedeaf on 2006-11-04
Hi all - my problem is I can't load ubuntu on live CD or access the existing Ubuntu partition. (CD boots and I can load kernel but then everything just freezes)
I got a new computer (MSI K9N Neo mobo, AMD 64, 320Gb SATA, CD/DVD on ide interface, etc.) and started setting it up in my usual way:

(hd0,0) Windows NTFS  (This partition was created manually within XP install)
(hd0,1) Ubuntu  EXT3  (The rest was manually created with ubuntus installation partitioner)
(hd0,2) Swap    SWAP
(hd0,3) DATA    FAT32

The thing is I somehow got live CD to boot once and made standard installation of Ubuntu Desktop i386 width mappings:

(hd0,0) /media/windows
(hd0,1) /
(hd0,2) swap
(hd0,3) /media/DATA

..but after reboot none of the ubuntu choices in grub works:
The interesting bits in my /boot/grub/menu.lst goes:

------------------------------------
  title  Ubuntu, kernel 2.6.17-10-generic
  root   (hd0,0)
  kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
  initrd /boot/initrd.img-2.6.17-10-generic
  quiet
  savedefaults
  boot

  title  Ubuntu, kernel 2.6.17-10-generic (recovery mode)
  root   (hd0,0)
  kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
  initrd /boot/initrd.img-2.6.17-10-generic
  boot

  title  Ubuntu, memtest86+
  root   (hd0,0)
  kernel /boot/memtest86+.bin
  quiet
  boot

  title  Other operating systems
  root

  title  Microsoft Windows XP
  root   (hd0,0)
  savedefaults
  make active
  chainloader +1
------------------------------

Trying to boot via grub standard "Ubuntu, kernel 2.6.17-10-generic":
  Error 17: Cannot mount selected partition
  (Somehow grub has written "root (hd0,0)" when it should be "root (hd0,1)" and on second line)

  ..so I manually edit the boot lines from:
  root (hd0,0) ..to.. root (hd0,1)
  (the third line seems to be wrong as well with ".. /dev/hda1 .." when it should be ".. /dev/hda2 .." or even ".. /devsda2 ..")
  No error message whatever numbers I edit to (hda1, hda2, sda1, sda2 etc.), only everything freezes just after boot screen appears (the progressbar thingy)

Trying to boot on live CD:
  (Note that all cd's and dvd's have been burnt multiple times on different speeds and all checksums md5's was checked, so this is not the problem)

  6.10 Edgy CD's and DVD's, all flavours (Ubuntu,Kubuntu,64bit,32bit, etc.) generate:
  No error message, everything seems ok until after kernel is loaded and bootscreen appears, only everything then freezes (the progressbar thingy) after a second or so

  6.10 Edgy release-candidate CD generate:
  Error message (I/O error - Error reading boot cd - Disk error 10, AX = 4280, drive EF) just after boot screen appears

  6.06 Dapper CD generates:
  A strange table looking like:

---------------------------------
..pstk....rstk
---------------------------------
.|.....|.:...........|
.|.....|0:ffffffff.5.|
.|.....|1:.....773.5.|0, drive EF
.|.....|2:....22e6.15|
0|.64.1|3:....2268.15|
1|..0.1|4:....2263.5.|
2|..0.0|5:....27c7.15|
3|.17.0|6:....27e4.15|
---------------------------------
.err 8
.ip. 262d : f.7
---------------------------------


..so:
I cant access the ubuntu partition
I cant load on any boot cd/dvd

How am I to get ubuntu to load ???????

I can acces the grub commandline but have tried things like:
root (hd0,1)
setup (hd0)
...etc. but nothing workes!

Anyone with any ideas???
Do I have to forget about ubuntu and go for Fedora???
Thanks / Stefan

---

### Post by timgood on 2006-11-04
The new Edgy kernel does not support Promise and some other SATA drives. I don't know why. They may be waiting for an updated kernel but there is no information about a fix or when those of us with these SATA controllers will be able to install. Dapper works fine with this MOBO, but Edgy Borks. My system got broke following the upgrade, and the only advice I have been given on the forum is to wipe and re-install Dapper. Hope this helps.

---

### Post by timgood on 2006-11-05
Does anyone know if a fix will be available soon for this? Would like to continue with Ubuntu rather than revert to Mandriva or Fedora.

---

### Post by Stonedeaf on 2006-11-05
Hey Guys I did it... =D =D =D
 Spent some precious saturday night hours on it with a friend and finaly got it running...

The problem ???

USB HUBS - Believe it or not but both me and my friend had waay trouble getting Ubuntu to boot/load/install or do just about anything...
The solution for my friend was to unplug his external HDD and an Usb hub. For me it was to inactivate the hub on my dell monitor and unplug just about all USB thingys except for mouse/keyboard...

Somehow these devises messed up the boot order/initiation/whatever or got in the way of  something (I still dont know exactely what was wrong) but unplugging them made the CD/DVD's boot just fine...

There was still the problem with the setup in menu.lst being way way wrong but this time, changing from...

root  (hd0,0)
kernel /boot/vmlinus-2.6.17-10-generic root=/dev/hda1 ro quiet splash

...to...

root  (hd0,1)
kernel /boot/vmlinus-2.6.17-10-generic root=/dev/sda2 ro quiet splash

...did have the desired affect and Ubuntu loaded just fine! =D

It was then a small thing to enter /boot/grug/menu.lst within ubuntu and manually setting this as default...

Never thought an usb thingy or two could do so mush damage! Worth mentioning I still had a small run in with the i386 version freezing after about 22% of file copy/installation so Im running the 64bit now... but my guess is that could be an cd error since I did drop the disk on the floor just before installation.. =)

Cheers n hope it helps someone... some admin/bugtracker should really look in to this USB thing !!!

/ Stefan

---

### Post by tancioste on 2007-01-02
I've had some issues trying to boot from Live CD, just before starting the X Server the system hangs.
I finally realized that the problem was related to the xorg configuration. It's quite simple to resolve, just enter in the console mode at boot using the break=bottom kernel parameter and change xorg.conf file. However it must be done every time you run the live cd.
Here is the complete step by step guide:
[http://iw0hnb.netsons.org/index.php?option=com_content&task=view&id=26&Itemid=31](http://iw0hnb.netsons.org/index.php?option=com_content&task=view&id=26&Itemid=31)

---

