---
title: "migrating root to MDRAID/LVM, blank boot screen"
date: 2011-12-06
forum: Installation &amp; Upgrades
---

### Post by kenyee on 2011-12-06
Anyone have tips on how to debug the boot process?

I think I shot myself in the foot migrating my root (11.10) over to MDRAID/LVM.
The original root was in two partitions...one /boot and the rest for root.
I added a 2nd disk, created two mdraid partitions (with the new drive but not the old) on it for /boot and lvm.
Then mounted up everything in a new /mnt/root dir, chroot'd to it, did an update-initramfs, then update-grub w/o errors.

It boots up, I can choose the kernel in the grub menu, checked the boot settings (though the set root command seems to be using a UUID instead of just "(md0)" but the vmlinux kernel is pointed to /dev/mapper/datavg-root as expected) and can't find anything wrong.

I tried adding "set debug=all" and got rid of "quiet nosplash" to see how far it got and it looks like it found the mdraid array, creates enough memory for the initial ramdisk, then jumps to it and....blank screen :-P

I'm surprised I can't even boot to the non-LVM kernel (it's on /dev/sda2 according to the grub menu).
Any suggestions?  I think update-initramfs failed to create a good boot ramdisk image is the only guess I have at this point...

I could reinstall, but don't want to lose all the configuration I've done..I've done this before w/ a Debian box, but never hit the blank screen issue...

---

### Post by darkod on 2011-12-07
You did the mdraid device with single disk only? What type of raid?

Apart from running update-grub from the chroot, did you run grub-install to install grub somewhere? Are you still using the old grub to boot?

---

### Post by kenyee on 2011-12-07
No, I'm doing using mdraid (raid level 1) with a new drive in the same system.
The way you do a migration of root is you add a new drive, set it up in degraded raid mode (new drive is raid with old drive marked "missing" so you can add it after you boot into your new raid setup), then move root over, do the chroot, do the update ramfs, grub, etc..
I was following this blog's notes: [http://www.pomeroy.us/2011/02/building-a-new-pvr/](http://www.pomeroy.us/2011/02/building-a-new-pvr/) and some of mine when I last did this to my other Debian box.

Yep, I did an install-grub and put it on both drives.
The grub menu does show the kernel on the LVM setup (verified by editing the entry) as well as the old kernel not on LVM...neither boot (you get the blank screen).
I also tried adding "debug" to the vmlinux line in the grub menu and nothing prints out.

When I did it on my Debian box and screwed up, at least it printed out messages about not being able to find /dev/mapper/datavg-root (meaning it was missing lvm), but this blank screen is giving me no clues :confused:

---

### Post by kenyee on 2011-12-09
FYI, I punted and reinstalled Ubuntu.
I tried the Repair Boot option in the Ubuntu Alternate CD w/o luck.  Found all the drives/partitions I set up while running that, then booted and....blank screen after selecting the kernel in grub... :(

Oh well, at least it wasn't that painful since it's a relatively new system...spent less time on the reinstall than trying to repair the boot issue :P

---

