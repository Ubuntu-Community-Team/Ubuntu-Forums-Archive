---
title: "Is it possible to get the ubuntu installer program on my normal install?"
date: 2013-11-12
forum: Installation &amp; Upgrades
---

### Post by ddanzeiser on 2013-11-12
I have a regular install of ubuntu 13.10 on my USB hard drive, but I want it to be able to act like the install disk too, and since it looked like the installer was a seperate program, is there any way to get this on my regular install?

---

### Post by ian-weisser on 2013-11-12
Look into the *ubiquity* packages. That's the current Live installer.

---

### Post by fantab on 2013-11-12
Not sure about regular Ubuntu install on USB acting as an installer, however the other way round is quite simple and more 'popular'.
If you burn the ubuntu.iso on USB with persistence with either 'startup disk creator' or 'unetbootin' then it works as both. Booting and running Ubuntu with 'persistence' is bit slower compared to full ubuntu install, though.

---

### Post by oldfred on 2013-11-13
I install from one hard drive to another as my standard way. But I have a /ISO folder on my drive and use grub to boot the ISO I want to install.

       This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

