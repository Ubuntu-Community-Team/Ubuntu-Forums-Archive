---
title: "grub freezing"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by jawaka on 2005-10-14
hi, just installed breezy (amd64) on my new box. installation went fine, but GRUB refuses to boot, hanging at the "please wait..." message. the scenario:

winXP, NTFS on (hd0,0) - breezy on (hd0,2)

tried booting by floppy, and at the grub prompt i can chainload windows normally.   seems that grub just can't read from linux partition. when issuing the command 'root(hd0,2)', it recognizes the ext2 partition, but after that, when i enter the command 'kernel' (even with correct params) it hangs. 'find' freezes also.

when booting from a liveCD, i can mount and see the linux partition without any problems. from there, i could reinstall grub to mbr. but when booting it just keeps hanging at the same point. checked all the parameters on the config file, and everything seems ok. 

any hints?

---

