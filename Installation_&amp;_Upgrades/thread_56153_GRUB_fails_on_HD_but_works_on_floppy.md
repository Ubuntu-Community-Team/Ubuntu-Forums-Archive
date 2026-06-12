---
title: "GRUB fails on HD but works on floppy"
date: 2005-08-11
forum: Installation &amp; Upgrades
---

### Post by jnoreiko on 2005-08-11
I have a system with 2 hard drives:
IDE0: 8GB parallel ATA
IDE1:  CDROM and a zipdrive
IDE2: 160GB SATA drive. Ubuntu sees this as /dev/sda

I installed Ubuntu to the SATA drive, and put GRUB in the MBR of the drive. However, on boot, GRUB says that it can't find the partition.
I went into GRUB console, did some rooting around, and it would appear that it thinks (hd1) is the zip drive -- at least, it's something it claims it can't find. What it *can* find is (hd2). But it gives strange results for the partitions on that (the one I expected to be ext3 was listed as ext2, for example). When I found something that looked like the ubuntu root partition and booted from it, I got a kernel panic from Ubuntu:

```

pivot_root: no such file
/sbin/int: 428: cannot open /dev/console/ no such file
``` 

However, what I also tried was installing GRUB on a floppy. I did this during the same installation process (I just ran the install GRUB phase twice).
Booting from the floppy is fine; and GRUB claims to be booting from (hd1,5) -- the root ubuntu partition.

What on earth is going on?

EDIT:

I tried GRUB's auto-complete to figure out what drives it thinks it can see.

Booting from floppy: fd0, hd0, hd1
Booting from HD: fd0, hd0, hd2, hd3

 :-?

---

### Post by amohanty on 2005-08-11
There seems to be an issue with GRUB on systems with both IDE and SATA drives. I posted a link to a workaround for this some time back. Ha found it:

[http://ubuntuforums.org/showthread.php?t=53396](http://ubuntuforums.org/showthread.php?t=53396)

The problem is not exactly the same in the thread but take a look at the link.

AM

---

### Post by jnoreiko on 2005-08-12
I've just managed to boot from HD.
I notes down my partitions from GParted and looked at GRUB's autocomplete listing.

When booting from HD, GRUB's hd0 and hd3 are THE SAME DRIVE, the SATA drive!
Booting from hd3 works.

Could GRUB be getting confused by my BIOS's boot order? I have the hard drives set to boot from IDE2 before IDE0.

---

