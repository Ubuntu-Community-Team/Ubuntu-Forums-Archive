---
title: "After install, no Grub?"
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by fizz on 2007-10-28
I initially had troubles booting the live cd, but found work arounds to get into gnome. After loading gnome, I had no panels which wasnt a big deal, I just wanted to install.

Went through the entire install, had me remove the cd and reboot. Upon reboot, vista loads.. Grub didnt modify my MBR for some reason. Any clues to why this is, and how to fix it?

AMD 64 X2 6000
MSI (nforce)
2gig ram
nvidia 8800 gts
sata hd

I have 3 partitions on the drive for windows (c,d,e)

setup a logical at end for swap and rest for /
so sda5 = / sda6 = swap

---

### Post by logos34 on 2007-10-28
possibility:
[http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect](http://www.users.bigpond.net.au/hermanzone/p1.htm#Turn_off_MBR_antivirus_or_write_protect)

try reinstalling grub from live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Or use vista boot manager to boot linux:
[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

---

