---
title: "Moving bootloader to another disk"
date: 2012-04-28
forum: Installation &amp; Upgrades
---

### Post by kjelle392 on 2012-04-28
After some trouble with installing Ubuntu (the automatically installation actually installed to an external hd without my knowledge), I finally made it working yesterday by makeing partitions myself and run the manual installationprocess. I can now boot both Ubuntu and Windows.

But; When I manually chose the installationpartitions, I missed on the bootloader - which I placed in a wrong hd... That means that I now have to go into bios and choose that drive every time I want to boot into Ubuntu.

I know I should reinstall, but is there a (simple) way to move that bootloader and merge it into the one on my systemdrive without loosing the opportunity to dualboot?

---

### Post by darkod on 2012-04-28
No need to reinstall. Simply boot ubuntu, and in terminal do:
sudo grub-install /dev/sdX

using the correct letter for the disk instead of X. That will install it on the MBR of that disk.

Further more, to double check with which disks grub2 is "connected", you can do:
sudo dpkg-reconfigure grub-pc

You should be able to select/unselect disks in the list. You select/unselect with Space bar. You do need to do the grub-install command above first.

---

