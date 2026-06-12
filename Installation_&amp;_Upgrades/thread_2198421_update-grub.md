---
title: "update-grub"
date: 2014-01-08
forum: Installation &amp; Upgrades
---

### Post by d.janse on 2014-01-08
solved

---

### Post by oldfred on 2014-01-08
I think grub2's os-prober mounts and tries to see if you have boot files or grub.cfg in every partition. What other partitions and do you have file corruption in any of them. May need chkdsk on all NTFS partitions and e2fsck on the Linux ext2 3 or 4 family of partitions. Do you have any special formats, RAID or LVM?

Is hard drive ok in Disks, or Disk Utility and Smart Status.

       Never force shutdown your laptop. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)
[http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274](http://ubuntuforums.org/showthread.php?t=1509765&p=12543274#post12543274)
[http://en.wikipedia.org/wiki/Magic_SysRq_key](http://en.wikipedia.org/wiki/Magic_SysRq_key)

---

