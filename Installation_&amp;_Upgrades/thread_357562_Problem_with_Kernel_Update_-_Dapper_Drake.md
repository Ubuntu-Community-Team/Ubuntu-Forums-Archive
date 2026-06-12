---
title: "Problem with Kernel Update - Dapper Drake"
date: 2007-02-09
forum: Installation &amp; Upgrades
---

### Post by Maverick88 on 2007-02-09
I just updated Dapper Drake using Synaptic.  Synaptic updated my kernel and initrd images etc.

But now when I reboot, I get this message:

root  (hd0,4)
    Filesystem type is ext2fs, partition type is 0x83
kernel /vmlibux-2.6.15-28-686  root=/dev/hda6  ro quiet splash
    [Linux-bzImage, setup =0x1c00, size=0x170551]
initrd  /initrd.img-2.6.15-28-686
    [linux-initrd  @  0x1f8ac000, 0x6a3fa5 bytes ]
savedefault

Error 15:  File not found

Press any key to continue...

I CANNOT get into X  / GNOME at all.

Help?  What can I do to get my Linux box back?

Rob

---

### Post by Maverick88 on 2007-02-09
I think I solved the problem.

I was able to boot into the RECOVERY mode.  Then at the command promt, I entered:

$sudo vim /boot/grub/menu.1st

I deleted the all the lines with "savedefault".

I saved menu.1st (i.e.  ESC :wq )

Now when I reboot, it works!   

This is very strange since my /boot/grub/menu.1st file had savedefault in it before and I had no problems booting.  But after the upgrade, the "savedeafult" lines gave me problems and grub would not boot the kernel.

Rob

---

