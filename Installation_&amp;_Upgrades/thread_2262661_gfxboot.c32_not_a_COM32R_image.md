---
title: "gfxboot.c32: not a COM32R image"
date: 2015-01-26
forum: Installation &amp; Upgrades
---

### Post by emiel606 on 2015-01-26
Hello,

I have problems with my HP t5630w (a thin client) when installing Lubuntu. When I boot the installer from my usb stick, it says this:

SYSLINUX 4.07 EDD 2013-07-25 Copyright (C) 1994-2013 H. Peter Anvin et al
Missing parameter in configuration file. Keyword: path
gfxboot.c32: not a COM32R image
boot:

I searched on the internet about this problem, and they say you have to press TAB and then type live. But when I type live and press enter, it just restarts. Is this because it is not powerfull enough? These are the specs:

VIA Eden 1,00Ghz
1Gb RAM
2Gb ATA flash storage
And i'm using a 4gb usb stick

Any help is welcome.

---

### Post by sbaig on 2015-01-26
I'm having the same problem when trying to install ubuntu server 14.10. I tried googling, and some people have suggested TAB --> select 'live'. all it tells me when i press tab is to check memtest. Can anyone explain this bug?

---

### Post by sbaig on 2015-01-26
solution: [http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701)

---

### Post by sudodus on 2015-01-27
> **sbaig said:**
> solution: [http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701)

That is one solution.

There is a fix for the bug of the ***Startup Disk Creator*** in that thread ([https://bugs.launchpad.net/ubuntu/+s...r/+bug/1325801]("https://bugs.launchpad.net/ubuntu/+source/usb-creator/+bug/1325801")), and it will trickle down to installed systems, but not to already released iso file versions. I guess Ubuntu 14.04.2 LTS (the second point release) of the iso file will be OK, and so will the corresponding iso files for Kubuntu, Lubuntu, Ubuntu Gnome, Xubuntu ....

The current ***Unetbootin*** works too. And there are installation tools, that were never affected by that bug, ***mkusb*** in linux and ***Win32 Disk Imager*** in Windows. See the following link (and links from it)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by emiel606 on 2015-01-27
When i create a bootable usb with win32 Disk Imager, it just bootloops. It restarts over and over again...
Is this because the thin client is not powerfull enough?

---

### Post by sudodus on 2015-01-27
I don't know much about thin clients.

Please describe with more details, and let us hope someone with more experience can chip in an help you.

How do you make the thin client boot from the pendrive?

Are you sure the thin client can boot from a pendrive?

What distro did you try to install? From what iso file? Still Lubuntu or some other distro? 32-bits or 64-bits?

Can you boot another computer from this pendrive?

Did you install Lubuntu into the pendrive according to this link: [https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

