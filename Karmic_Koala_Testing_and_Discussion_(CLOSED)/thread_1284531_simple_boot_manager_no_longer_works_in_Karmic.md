---
title: "simple boot manager no longer works in Karmic"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by michael37 on 2009-10-06
SBM is a nice hack which allows booting from devices that BIOS doesn't properly support, for example, from some USB CD-ROMs or from diagnostics dell partition.

In Jaunty and earlier releases, using SBM was trivial (inspired by [http://www.gentoo-wiki.info/GRUB/Chainloaded_CD-ROM](http://www.gentoo-wiki.info/GRUB/Chainloaded_CD-ROM), but no downloads required).  Simply install package syslinux, copy file /usr/lib/syslinux/memdisk to /boot; then copy file /install/sbm.bin from any Ubuntu install CD to /boot (reference: [https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)).  Finally, set up grub 1 entry 
```

title SBM
root (hd0,1)
kernel /boot/memdisk
initrd /boot/sbm.bin

```

The same strategy doesn't work for Karmic.  I added the following entry to /etc/grub.d/40_custom
```

menuentry "SBM" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 1017bb9e-ad12-494f-a580-6f94b015891d
	linux /boot/memdisk 
	initrd /boot/sbm.bin
}

```

When I try to choose this entry in grub2 menu, I get one line of text as if kernel is trying to boot, then screen blanks and computer hangs.

I tried using memdisk and sbm.bin from both Jaunty and Karmic under Karmic and neither work.

---

