---
title: "[SOLVED] installing windows"
date: 2008-06-08
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2008-06-08
hi there
I had ubuntu on my computer and I want to install win as a second OS. I know that installing win after Linux is a little tricky. As I know win rewrite the master boot partition, but I want to keep my Linux as a primary OS. 

Any help

thanks a lot

---

### Post by housam on 2008-06-08
you have to make a free space to windows. using Gparted from ubuntu live cd 
resize ubuntu partition leaving an unallocated space.
format the new partition to ntfs format .
install windows on that partition.
[[COLOR="Red"]_reinstall grub_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

