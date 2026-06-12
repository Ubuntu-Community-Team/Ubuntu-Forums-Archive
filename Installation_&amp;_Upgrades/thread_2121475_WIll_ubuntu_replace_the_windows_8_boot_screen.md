---
title: "WIll ubuntu replace the windows 8 boot screen?"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by Andrewknowslinux on 2013-03-02
Hello, i have installed ubuntu many times on seperate partitions with a dvd or a flash drive with windows 7 and older and it worked fine. However i had to get a new hard drive because mine cracked. Anyway i'd like to install ubuntu again on a seperate partition nothing else and i was just wondering would ubuntu replace the windows 8 boot screen with grub? because i just dont want grub on there. Oh and i do not have an UEFI bios.

---

### Post by darkod on 2013-03-02
If you have only one disk and you don't install grub2 to the MBR, what will boot ubuntu? Windows bootloader can't do it.

There are some work arounds but I always recommend grub2 on the MBR. The only exception are special cases. Grub2 is not designed to be installed onto a partition and chainloaded from the windows bootloader. It doesn't fit on the partition boot sector, so it has to put part of the files inside the root partition. But during major upgrades to the grub2 package, these files move and it will not know where to find them after that. You might need to reinstall grub2 after every major upgrade (once again, to the package, not the ubuntu version).

If you really want to do this, you can use the manual install method and tell grub2 to install onto the root (or /boot if it exists) partition, and then configure windows bootloader how to chainload to it.

In most cases, the best solution is grub2 to the MBR.

---

