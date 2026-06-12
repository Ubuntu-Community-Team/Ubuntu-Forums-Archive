---
title: "Can not boot from second hard drive"
date: 2011-06-26
forum: Installation &amp; Upgrades
---

### Post by aravot on 2011-06-26
I (new user) am using Ubuntu 11.04 and disconnected that hard drive to load Debian on a second hard drive. Now when I plug in the Ubuntu drive it will not load. Is this a problem with "grub" and what must I do to boot my original Ubuntu drive?

---

### Post by Quackers on 2011-06-26
Which hard drive is set to boot first in your bios? Play with that.

---

### Post by Elfy on 2011-06-26
I'd assume that debian installed it's bootloader, if that's grub legacy it'll be a matter of just editing menu.lst and addung the ubuntu to it. [Alternatively reinstall the ubuntu bootloader]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

Would have been easier to not disconnect the other hard drive I expect :)

---

