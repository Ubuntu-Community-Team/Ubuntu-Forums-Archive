---
title: "Error: Cannot boot the OS"
date: 2007-07-09
forum: Installation &amp; Upgrades
---

### Post by Onay on 2007-07-09
Here's a quick synopsis: I installed ubuntu 7.04 on an external hard drive. My MBR got all messed up and GRUB apparently was trying to boot Windows on my internal drive running XP. So I restored my MBR back to it's original state using a program called MBR fix. When I go to boot the external drive in the BIOS now, I get an error message reading...
```
Error booting the operating system
```
I'm not sure how restoring the MBR removed GRUB from the external drive, but it seems to be the case. The only other explanation I can offer is that GRUB was installed on my internal drive used to boot the external drive thereafter. How can I reinstall only GRUB on ONLY the external drive? Any help is much appreciated!

---

### Post by Pumalite on 2007-07-09
Check this:

[http://users.bigpond.net.au/hermanzone/p12.htm](http://users.bigpond.net.au/hermanzone/p12.htm)

And this:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

