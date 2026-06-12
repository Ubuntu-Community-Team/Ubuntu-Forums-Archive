---
title: "dual boot gentoo and ubuntu"
date: 2008-02-12
forum: Installation &amp; Upgrades
---

### Post by dendixon on 2008-02-12
Just installed ubuntu 7.10 on an empty partition and left my gentoo 2.4.26 in a different partition.

Ubunu boots fine, but when I try to boot gentoo it starts to boot then I get these messages:

Trying to move old root to /initrd ..okay
Mounted devfs on /dev
Freeing unused kernel memory:  88k freed
FATAL: kernel too old
kernel panic: Attempted to kill init!

My guess is when ubuntu rewrote grub it installed a different initrd or something like that that won't run my gentoo.

A second problem is all my files are in the gentoo /root directory which when I go to in ubuntu it says I don't have permission to access.  So I can't get at any of my work.

Thanks for any help.

---

### Post by dendixon on 2008-02-12
Not that big a deal, just scary when nothing worked.

Apparently, ubuntu doesn't use grub.conf on the /boot partition, but uses 
/boot/grub/menu.lst in the ubuntu partition. Ubuntu never touched my grub.conf file.

Just copied the entry to boot my gentoo

****
title=Gentoo Linux 2.4.26-r9
root (hd0,0)
kernel /kernel-2.4.26-gentoo-r9 root=/dev/hda4
****

 from grub.conf to menu.lst and everything works fine.:

---

