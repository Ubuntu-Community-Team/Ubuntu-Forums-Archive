---
title: "usb boot disk programs"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by tothextreme on 2010-06-06
Hello,
I have this new found passion for Linux and gathering lots of good info from this site and others. Running Ubuntu 10.04 currently. But for some reason cant seem to find what im looking for about making USB drives bootable once ive downloaded the .iso file i want. USB-creator-gtk seems to only work with the ubuntu family. ImageWriter only works with .img files? I want to play around with other linux distros from .iso. I tried makebootfat and got some errors. ill post them later if you guys think makebootfat is the way to go but i think im making it to too hard on myself. 
Thanks!

---

### Post by oldfred on 2010-06-06
There are a variety of ways to create bootable USB flash drives. You can use unetbootin, pendrive and others that use a FAT based system.

You can copy grub to a USB drive & make it bootable. And then copy many ISOs to it. Or you can do a full install of just about any linux to a flash drive if it is large enough.

I have a USB with 4 ubuntu iso, system rescue & gparted iso and use grub to boot. I use some of panticz (which is a full script and the ky links)

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)

---

### Post by dandnsmith on 2010-06-06
An easy first step is to consult [pendrivelinux](http://www.pendrivelinux.com/) to get methods and assistance with the necessary processes.

HTH

---

