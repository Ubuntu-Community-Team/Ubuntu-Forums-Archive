---
title: "Dual boot Ubuntu with XP installed on a RAID 0 array."
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by kevpatts on 2007-05-23
Okay, before you ask, I'm not trying to install Ubuntu on the RAID array!

I have two 320gb SATA2 drives (/dev/sda & /dev/sdb) drives raided together (RAID 0) with XP on them, and one 120GB IDE (/dev/hdb) drive that I'm looking to intsall Ubuntu on.

I can successfully install and run Ubuntu if I set my PC to boot from the IDE drive first, but then I don't have dual boot functionality and have to swap over in the bios every time I want to boot a different OS.

If I set the system to boot from the SATA RAID array and try to install Ubuntu I don't get a grub screen after installation completes. I booted into Ubuntu (by setting the bios to boot from the IDE drive) and followed instructions to build a boot sector file to be used by Microsoft's boot loader (using c:\boot.lnx="Ubuntu" in boot.ini). If I try to boot into Ubuntu this way I get a message saying "GRUB" and nothing else.

The other road I looked to go down was directly installing grub onto the start of the array (/dev/sda) but for this i need to know what drive this is in (hd0) format, which I don't know how to find out.

Thanks for any help in advance,
Kevpatts

---

