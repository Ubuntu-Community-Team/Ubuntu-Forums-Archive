---
title: "grub2 dosn't save windows as last selected + boot into cdrom from grub2"
date: 2010-05-17
forum: Installation &amp; Upgrades
---

### Post by PackElend on 2010-05-17
I went through so  many post but I haven't found the proper answer yet hope you have an  Idea

1. Grub2 saves only Linux OS as last selected no Windows OS

2.It  is possible to boot into a cdrom (drive)?

thx

stefan

---

### Post by MichealH on 2010-05-17
Solution for 1) In Ubuntu goto termial and type in ```
sudo update-grub
```
When done restart and tell me how it went.

Solution to 2) You cannot boot into CDROM on Grub 2 if you have the BIOS settings correct then you can boot into CDROM before GRUB 2.

---

### Post by oldfred on 2010-05-17
If you want you can directly load the ISO file from grub. You do not have to install it to a Cd. Works from hard drive or USB.

MultiBoot USB with Grub2 (boot directly from iso files)
[http://www.panticz.de/MultiBootUSB](http://www.panticz.de/MultiBootUSB)
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntuforums.org/showthread.php?t=1451184](http://ubuntuforums.org/showthread.php?t=1451184)
[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html#cli_loopback)
[http://ubuntuforums.org/showthread.php?t=1224417](http://ubuntuforums.org/showthread.php?t=1224417)

---

