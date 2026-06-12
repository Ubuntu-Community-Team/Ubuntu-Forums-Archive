---
title: "trouble using boot CD"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by smitty96 on 2010-11-04
OK, so the 10.10 CD boots, but the installer doesn't. It shows the loading screen, but then it just goes black. My monitor shows a message something along the lines of "out of scan range". What does this mean? The same thing happens if I try to boot from a Chrome OS CD.

---

### Post by oldfred on 2010-11-04
Have you tried any parameters?

[SOLVED] How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

Check BIOS for settings and sometimes other parameters:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

