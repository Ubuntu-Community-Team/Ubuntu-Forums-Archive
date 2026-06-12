---
title: "Reordering partitions - GRUB"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by Quatrix on 2008-05-04
I'm using GRUB to dual-boot XP Pro and Ubuntu 8.04.  I want to reorder my partitions for no particular reason, so my Linux partition (including GRUB configuration) changes from (hd0,6) to (hd0,7) or something like that.  GRUB gives "Error 17" at boot, I'm assuming because the boot loader points to the old location.  What's the easiest way to point it to the new partition ID?  I found a lot of answers around the web, but they seem overly complicated and risky.  This seems like it should be simple.

---

### Post by logos34 on 2008-05-04
On the grub screen press 'e' to edit, 'e' again on the 'root' line and change it.  Then 'enter; and 'b' to boot.  WHen you find an entry that gets you into ubuntu make the change permanent:

gksudo gedit /boot/grub/menu.lst

---

### Post by Quatrix on 2008-05-05
> **logos34 said:**
> On the grub screen press 'e' to edit, 'e' again on the 'root' line and change it.  Then 'enter; and 'b' to boot.

GRUB hangs with Error 17 without ever going into the boot menu.  The 'e' and 'c' keys don't seem to work from there.  To clarify, I have no trouble editing menu.lst to point to the new Ubuntu partition.  The problem (I think) is getting the master boot record to point to the moved partition, which contains the GRUB configuration.

---

### Post by logos34 on 2008-05-05
> **Quatrix said:**
> GRUB hangs with Error 17 without ever going into the boot menu.  The 'e' and 'c' keys don't seem to work from there.  To clarify, I have no trouble editing menu.lst to point to the new Ubuntu partition.  The problem (I think) is getting the master boot record to point to the moved partition, which contains the GRUB configuration.

oh, ok, thought you were getting the grub menu.

In that case, reinstall stage1 to the mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

