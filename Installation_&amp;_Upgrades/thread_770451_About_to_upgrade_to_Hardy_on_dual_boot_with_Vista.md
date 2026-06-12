---
title: "About to upgrade to Hardy on dual boot with Vista"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by Neil_The_Newbie on 2008-04-27
Advice Needed Please: I currently have my laptop setup as a dualboot with Vista and Ubuntu 7.10. I'm about to upgrade Ubuntu to 8.04 -is there anything i need to be aware of before I do this as its dual boot?

Thanks in advance.

---

### Post by Rallg on 2008-04-27
I don't recall seeing any issues related to that, during beta testing phase. A lot of testers did an upgrade, and many (such as myself) also dual-boot with Vista. There's always the possibility that HH may do something (or fail to do something) that you had in GG, but it would be unrelated to dual boot.

It is probably best to upgrade via command line from within GG:
sudo apt-get update && sudo apt-get dist-upgrade
You might consider changing your software repositories to one of the mirrors, if your existing repository is slow. Right now, there is heavy demand. Also be sure that your repository list will deliver Hardy, not just Gutsy.

If you decide to erase your existing GG and install fresh Hardy from CD, then the partition's UUID will be changed during its reformat. This is only of interest if you have Grub bootloader in a place where it is not automatically updated by the CD installation. If, so, be sure to manually edit your menu.lst to reflect the change, as well as the new kernel number.

---

