---
title: "Small /boot partition"
date: 2024-10-14
forum: Installation &amp; Upgrades
---

### Post by tilkov on 2024-10-14
Hi everyone,

I've got this Ubuntu system which was installed a couple of LTS versions ago and upgraded ever since.
The partition layout (created by the installer long time ago) is:

/dev/sda1: 228 MB /boot
/dev/sda2: 350 GB LVM volume group with / and swap as logical volumes inside

It is time to update to the next LTS, but even with one kernel inside, the /boot partition does not have enough free space (146 MB needed). 

My question is how to i move the LVM and its partition /dev/sda2 to the right by 200-300 megabytes so there is space to extend /dev/sda1 (/boot).

Things I've tried:
Booting LiveCDs with GParted, KDE Partition Manager and Blivet-gui - they do not seem to be able to resize the volume group from the left. I can only extend it to the right. Maybe I am doing something fundamentally wrong (haven't dealt with LVM much).

Ideas welcome.

---

### Post by ActionParsnip on 2024-10-14
is /boot on LVM?
If you uninstall old kernels it'll free up space on /boot

---

### Post by tilkov on 2024-10-14
No, /boot is not on LVM, it is on /dev/sda1, a normal partition in front of LVM which is /dev/sda2.
All old kernels are uninstalled, only the currently running kernel resides in /boot. I cannot free anymore space.

---

### Post by Dennis N on 2024-10-15
Some thoughts on what you might do. You really need a working knowledge of LVM commands to do most of this.

You need to add another PV sda3 to the VG so that you can move the contents of PV sda2 to it (with pvmove). Then you can remove PV sda2 from the VG (with pvremove) and delete it, making room to expand sda1.

Is there space after sda2 to create another PV large enough to hold the contents of sda2? If not you have to shrink PV sda2 to create enough free space. Try with gparted.

After all that, you can create a new PV in the space between sda1 and sda3 and add it to the VG to restore the unused space back into the VG.

Where did you get the blivet-gui package for Ubuntu?

---

### Post by TheFu on 2024-10-15
If it were me, I'd buy a new SSD and migrate the PV to it using **pvmove**.  This can be done while the system is online. All VGs and LVs in the PV will be migrated as well.  I've done this myself.  While you are at it, create a new 700MB  /boot partition (and perhaps a 100MB FAT32 partition for UEFI booting).  

You can migrate those to the new SSD too and then setup a chroot,  fix the fstab mounts and install grub to the new SSD.  Next remove the old storage and try to boot.  These steps will need to happen using a Try Ubuntu environment.  But if you just move the PV to new storage, you'll have all that room on the original storage to expand /boot into - more than enough.  Since a quality 500G SSD is just $60, this isn't exactly costly.

It comes down to how risk adverse you are for having loss of system use and possibly being forced to do a fresh install and restore from backups.

For mounted LVM, I use the /dev/{vg-name}/{lv-name} symlinks, so you'll only need to worry about the new UUIDs for /boot and whatever the EFI thing is, if you use it.

If you'd like to modify your LVM layout, this would be a good time to reduce the LVs that are much too large.  Always remember, the real power in LVM is flexibility and that flexibility comes only when there is unused space in the VG.

---

### Post by tilkov on 2024-10-16
@Dennis N This is the best idea so far, I think I'll go with that.

> **Dennis N said:**
> 
Where did you get the blivet-gui package for Ubuntu?


I didn't, used a Fedora iso.

---

### Post by georgesgiralt on 2024-10-16
Hello,
If your LVM PV has free space, you have to create a new LV of, say 1GB, format it as EXT4 and mount it as /boot instead of the /dev/sda1.  Mount /dev/sda1 as /test or /mnt and copy it's content into the new /boot. 
Once this is done, you have to do update-grub and redo the initramfs  for your kernel. 
And then reboot. If everything goes to plan, you've got a full LVM install and a large enough /boot. 
Hope this helps.
P.S. : this layout was used long ago because Grub did not understand LVM and, thus, could not find /boot if in LVM system. This is long gone and now, Grub can understand the layout of LVM schemes.

---

