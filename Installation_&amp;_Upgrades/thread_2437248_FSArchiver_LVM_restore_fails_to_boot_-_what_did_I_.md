---
title: "FSArchiver LVM restore fails to boot - what did I miss?"
date: 2020-02-20
forum: Installation &amp; Upgrades
---

### Post by ltburch2000 on 2020-02-20
So I have a 19.10 Ubuntu ext4 LVM system which has just the root and swap partitions no separate boot partition.  
Device           Start       End   Sectors   Size Type
/dev/nvme0n1p1    2048   1050623   1048576   512M EFI System
/dev/nvme0n1p2 1050624 488396799 487346176 232.4G Linux LVM

I have been backing up by taking LVM snapshots and then using fsarchiver to archive that snapshot.  The idea being to recover I can just run a ubuntu installer and install a LVM ubuntu fresh then lay my file system down from a backup.
However when I do this it fails to boot, saying there is no boot loader.  Previous to this I was able to boot off the fresh install.
One notable thing is that in the most recent ubuntu installer it now names the LVMs a little differently than before
New:
  --- Physical volume ---
  PV Name               /dev/nvme0n1p2
  VG Name               vgubuntu
  PV Size               232.38 GiB / not usable 2.00 MiB

Old:

  --- Physical volume ---
  PV Name               /dev/sdc5
  VG Name               ubuntu-vg
  PV Size               <232.17 GiB / not usable 2.00 MiB

So the VG changed name, I can change that to match

LVs are relatively speaking the same

New:
  --- Logical volume ---
  LV Path                /dev/vgubuntu/root

Old:
  --- Logical volume ---
  LV Path                /dev/ubuntu-vg/root

So if I rename the VG from vgubuntu to ubuntu-vg and restore the file system image I should be OK right?  However when I boot it says there is no boot loader.  Where am I going wrong?  Is it some problem with the mapper?

---

### Post by Dennis N on 2020-02-20
This may apply to your situation:

If you rename a volume group, the initramfs on startup is still using the old volume group designation in the device name for all LVs in the VG. They won't boot. The way to fix this was to chroot into the broken system(s) from live media (or an unaffected install, if any) and update the initramfs.

---

### Post by ltburch2000 on 2020-02-20
> **Dennis N said:**
> This may apply to your situation:

If you rename a volume group, the initramfs on startup is still using the old volume group designation in the device name for all LVs in the VG. They won't boot. The way to fix this was to chroot into the broken system(s) from live media (or an unaffected install, if any) and update the initramfs.

Yeah, I did do an initramfs and I checked and saw that it had in fact generated a new image, update-grub would not work but I assumed that was because I was in a quasi in between place and my manual execution of the initramfs should straighten out the boot.  I also directly editing the grub.cfg to reference the new VG.

Though I think your point about a chroot after restore and rerun initramfs might just do something for me.

---

### Post by ltburch2000 on 2020-02-20
I have a plan, does this sound like it will work?

Boot to install CD, install 19.10, boot to new 19.10 to test for good measure.  Update if needed.

Boot to install CD again, copy /boot and fstab from working disk to backup dir on install USB - plenty of room.

fsarchiver restore to file system, cp the boot and fstab backup back to disk overwriting copy from fsarchiver

Reboot to new image - profit?!?!?

---

### Post by Dennis N on 2020-02-21
I'm not familiar with the tool fsarchiver, but when I made the same mistake, I used chroot and update-initramfs -u, rebooted and the system then booted correctly. But clearly your situation is more complex according to your post #1 description, and I'm unable to analyze that. That's why I said in the initial reply that the information "may apply to your situation". 

Anyway, I hope you have worked it all out by now.

---

### Post by ltburch2000 on 2020-02-24
Nope, could not get anything to work.  Eventually just started clean and set up most everything over again.  Still had the drive image so I could copy config files for a lot of things.

---

### Post by The Cog on 2020-02-24
I have done that in the past, but without the complication of LVM. I had to to two things: First, use the live CD to run grub-install (the GRUB bootloader goes outside the partition you are restoring, either in the MBR or a UEFI partition), and secondly, edit fstab to correct the UUID of the boot partition - fsarchiver does not preserve the partition UUID.

---

