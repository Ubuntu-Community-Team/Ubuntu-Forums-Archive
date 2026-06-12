---
title: "Installing 32bit distro onto HD from a 64bit Live boot"
date: 2016-08-12
forum: Installation &amp; Upgrades
---

### Post by debiruman665 on 2016-08-12
I am trying to revive and old point of sale system with a touch screen that previously ran on windows XP. It's no longer supported anymore and it generally runs like crap. I've formatted the hard drive and I need to install the 32bit version of ubuntu. Every machine I have is 64 bit and no matter if I burned the 32-bit version to a USB drive or a disk I just can't get any machine to load it up. The point of sale system did boot ubuntu but the transfer speeds from what is most likely USB ver.1 makes it almost impossible to even load it up.

I had removed the hard drive and put it into an enclosure so I can access it with USB. 

Is there any way I could live boot up a 64bit version of ubuntu but write a 32bit installation onto that drive?

At that point, I plan to just put the HD back into the point of sale system and let it boot up that way.

---

### Post by ajgreeny on 2016-08-12
No, you can not boot to a 64bit live OS and install a 32bit version from that; if it is a 64bit live system it will install a 64bit OS to your hardware.

How are you trying to "burn" the 32bit version to a USB; maybe that is the problem we need to solve first?

---

### Post by sudodus on 2016-08-12
I think it is a good idea to do what *ajgreeny* suggests, to make a 32-bit boot DVD or USB drive with Lubuntu, Xubuntu or Ubuntu MATE, which are lighter than standard Ubuntu and therefore better for an old computer (of the Windows XP era). Boot from that drive and install the system into the hard disk drive. If you avoid proprietary drives, the hard disk drive should be portable, and boot in your old computer.

You can also try according to one of the following links,

[Tested and debugged system to install [Ubuntu flavours of] Xenial 32-bit alias 16.04 LTS](https://ubuntuforums.org/showthread.php?t=1958073&page=19&p=13511300#post13511300)

[https://help.ubuntu.com/community/OBI](https://help.ubuntu.com/community/OBI)

[OBI/Xenial-32-txt](https://help.ubuntu.com/community/OBI/Xenial-32-txt)

---

