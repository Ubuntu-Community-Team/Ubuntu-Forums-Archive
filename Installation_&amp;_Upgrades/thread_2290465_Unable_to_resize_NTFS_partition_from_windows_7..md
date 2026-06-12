---
title: "Unable to resize NTFS partition from windows 7."
date: 2015-08-12
forum: Installation &amp; Upgrades
---

### Post by guillermo12 on 2015-08-12
Hi, I have a PC that want to resize a 500Gb partition which already contains a Windows 7.

I booted with gparted live CD but I can't resize the partition, only 1 byte before or after. Here is an attachment of the Partition editor.

What could I do??

Thanks!

---

### Post by dino99 on 2015-08-12
i've read somewhere that a gparted version was having that 'one byte' issue (might be fixed with the latest gparted live version)
but you should shrink the windows partition(s) with the Windows tool

[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

---

### Post by Mark Phelps on 2015-08-12
Use Disk Management in Win7 to do the resizing.  It might require a reboot to do that.

IF that does not work, use the free version of the Minitool Partition Wizard.

---

