---
title: "grub issue"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2010-05-04
I recently upgraded to 10.04. The grub menu shows my windows partition but does not load it when I select that OS.

---

### Post by _0R10N on 2010-05-04
You might try running
```
update-grub
```
another way is reinstalling grub, that will force a re-detection of your bootable partitions.

---

### Post by oldfred on 2010-05-04
Fix for most, a few have other issues:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

This is what the instructions say:
If you're unsure which **drive** is designated as boot drive by your BIOS, it is often a good idea to install GRUB to all of them.        

It also says:
Note: It is possible to install GRUB to **partition** boot records as well. However, this forces GRUB to use the blocklist mechanism, which makes it less reliable, and therefore is not recommended.

It then presents a check box with** all drives and partitions**. So everyone (And I think it its everyone) checks all the boxes. Only drives sda, sdb, etc should be checked. Not partitions sda1, sda2, sdb1, etc.

Installing to the windows partition overwrites part of the windows boot that is already in the windows boot sector or PBR.

---

