---
title: "Ubuntu 8.04 doesn't install"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by quincasmetall on 2008-08-06
Hello, there!

About two months ago i've trying to install the recent version of Ubuntu in my PC, without success. 

I've downloaded the ISO in a lot of sources and types (alternate, desktop; including the UbuntuStudio distribution), and burned in cd's, following the required recomendations.
But even so, i got an unsucceful result trying to install in so many times. When it starts the file copy to the hard disk, the instalation progress stops. (generally about 20~25% of progress)

Ps: Im using ext3 file system.

Ps2: Sorry about my english.

---

### Post by spiderbatdad on 2008-08-06
Have you been able to boot the live cd? That is run it without actually installing it?
You may have to try some "boot options" by selecting F6 from the startup screen. You then delete the end of the boot line: "--quiet splash" and type in some various options. What will work is uncertain, perhaps: noapic
or noapic nolapic.
See this guide, though do delete quiet splash.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If boot options work, you make them permanent by editing the file /boot/grub/menu.lst after the installation is successful.

---

### Post by quincasmetall on 2008-08-07
> **spiderbatdad said:**
> Have you been able to boot the live cd? That is run it without actually installing it?
You may have to try some "boot options" by selecting F6 from the startup screen. You then delete the end of the boot line: "--quiet splash" and type in some various options. What will work is uncertain, perhaps: noapic
or noapic nolapic.
See this guide, though do delete quiet splash.
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If boot options work, you make them permanent by editing the file /boot/grub/menu.lst after the installation is successful.


Yes, i can boot live cd normally.

---

