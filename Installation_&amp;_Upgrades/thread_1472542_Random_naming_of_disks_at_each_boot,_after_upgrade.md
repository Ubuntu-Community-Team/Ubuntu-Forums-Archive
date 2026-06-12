---
title: "Random naming of disks at each boot, after upgrade to 10.04"
date: 2010-05-04
forum: Installation &amp; Upgrades
---

### Post by Etienne53 on 2010-05-04
Hi all,

After upgrade to 10.04, my disks are randomly named (sda, sdb, sdc) at each boot. My drive labeled "XP" is sometimes named "sdb" and sometimes "sdc", while my other drive "DATA" is respectively "sdc" or "sdb". This wasn't the case before upgrade with KUbuntu 9.10.

Due to this random naming, my auto-mount in fstab often fail at boot time !

Any solution for this (not found here by myself) ?

Is this linked to Grub troubles reported many times here ?

:confused:

---

### Post by psusi on 2010-05-04
Fix your fstab to use UUID instead of naming the device directly.

sudo blkid will show you the UUIDs of detected filesystems, then replace /dev/sdwhatever in fstab with UUID=xxxx.

---

### Post by Etienne53 on 2010-05-04
> **psusi said:**
> Fix your fstab to use UUID instead of naming the device directly.
sudo blkid will show you the UUIDs of detected filesystems, then replace /dev/sdwhatever in fstab with UUID=xxxx.

OK, thanks... It will certainly solve the auto-mount trouble.

But, I don't like the idea that my drives are named randomly at each boot... I guess this will be the source of some other troubles and instabilities. 

I hope this behavior will be updated soon !

;)

---

### Post by psusi on 2010-05-04
> **Etienne53 said:**
> 
I hope this behavior will be updated soon !

;)

Nope, the behavior is intentional.  Hardware is now scanned in parallel, so the exact order in which it is detected can vary from boot to boot.  This is why UUIDs were introduced.

---

### Post by Etienne53 on 2010-05-04
> **psusi said:**
> Nope, the behavior is intentional.

:(:(:(

---

### Post by efflandt on 2010-05-04
Maybe that accounts for my problems attempting to boot 10.04 LTS full install from USB on on one computer (desktop), when it boots fine on two completely different laptops.  How does grub2 in the mbr tell which disk is which to find its other files and menu?

For example in grub.cfg on the USB drive, that drive ends up as (hd1) with Linux on (hd1,2).  From grub rescue prompt on the desktop, it appears to be (hd0) in which case Linux should be (hd0,2).  But the initial grub error (before it even gets to any menu) is unknown filesystem (it is ext3).  And **ls (hd0,2)/** cannot access anything.

If I **sudo update-grub** on my main hard drive (from karmic), then it cannot find the USB drive by its (correct) UUID.

The install iso boots fine from CD or USB flash on the PC that cannot boot the full 10.04 on USB hd.  Karmic also boots fine from USB hd on that PC, it is just Lucid that fails.

---

