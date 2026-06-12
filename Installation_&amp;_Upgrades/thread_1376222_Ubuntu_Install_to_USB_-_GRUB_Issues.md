---
title: "Ubuntu Install to USB - GRUB Issues"
date: 2010-01-08
forum: Installation &amp; Upgrades
---

### Post by darrengreer on 2010-01-08
I have a netbook, that I'm attempting to install ubuntu to a USB to boot from and run (Can't install to the internal drive for other reasons).  Anyway, I have two USB drives, one with the Live 9.10 version of Ubuntu. So, where is what I have done so far:

-Boot off of the live USB (/dev/sdb).
-Mount, then install to secondary USB (/dev/sdc)
-During install, install grub to /dev/sdc USB drive
-Install appears successful.

Now the fun begins.  When I try to now boot off of the installed to USB (the live USB is not plugged in).  Grub comes up fine, but upon trying to boot, get an error like:

```

kernel panic - not syncing : VFS: unable to mount root FS on unknown-block

```

I have a feeling it may be something to do with the fact that it was /dev/sdc with two USBs installed, but now with only one, it might be /dev/sdb.  However, I've edited the grub menu and changed "set root" and tried (hd0,0),(hd0,1),(hd1,0),(hd1,1),(hd2,0),(hd2,1), with no luck.  I've also tried changing the kernel line for each of these options to /dev/sdb1 and /dev/sda1, with always the same error.

I found a recommendation to add rootdelay, so I tried each option with that as well, with no luck.  I don't know what else to try at this point.  I have even booted from the live USB, chroot'ed to the installed to USB, and modifed grub.cfg and device.map to each of these different configurations and re-ran update-grub to no avail.  With device.map, I tried hd0 mapped to /dev/sdb and /dev/sdc, or hd1, etc., with no luck.  

What am I missing?  Thanks!!

---

### Post by darrengreer on 2010-01-09
Tried every USB port, just to be safe...no luck.

Any thoughts?

---

### Post by darkod on 2010-01-09
What happens if you select the recovery mode entry in grub menu? Keep the usb stick unplugged and try the recovery mode.
If you manage to get to command prompt, try
sudo update-grub

Reboot and see what happens.

---

### Post by darrengreer on 2010-01-10
> **darkod said:**
> What happens if you select the recovery mode entry in grub menu? Keep the usb stick unplugged and try the recovery mode.
If you manage to get to command prompt, try
sudo update-grub

Reboot and see what happens.

THanks for the tip... While it didn't solve the problem, it led me to finding the problem.  The USB memory stick, was a Sandisk Cruzer.  For whatever reason, they partion that thing very funny, with some U3 partition.  I used their uninstaller, to remove the U3 partition, and even tried to partition it myself, but every time, looking at recover mode, I could see that the device was not mounting.

As such, I tried a different USB flash drive, and all worked well.

Thanks

---

