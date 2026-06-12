---
title: "Should I mirror the &quot;bios-grub&quot; partition for software RAID1 install?"
date: 2012-11-12
forum: Installation &amp; Upgrades
---

### Post by OneOfMany07 on 2012-11-12
I'm trying to set up software RAID 1 for my OS drive using 2 x 3TB drives.  I was planning to use the alternative installer and manually create the MDA devices linking the guided partitions that were created on each individual device.  I tried the "make a single partition" idea, but there isn't a guided option for the partitions already in a RAID device.

The question I had was with the 3TB drive I have a 1MB "bios-grub" partition.  I think I roughly understand what it is for (I must have a GPT partition not MBR with this >2TB drive), but I'm not sure if I'm supposed to mirror that partition to make it fault tolerant like I did with swap and /.  Part of me thinks yes, but part thinks the info could be drive specific and using UUID's or something.

---

### Post by oldfred on 2012-11-12
I do not know RAID, but I would think you have to mirror it. It is where grub puts the core.img.

In a GPT partition map, the 31 kiB area after Master Boot Record where GRUB is usually embedded to, does not exist. When GRUB can't be embedded, its only option is to use blocklists, which are unreliable and discouraged. Thus, you must make a separate "BIOS boot partition" to hold core.img. BIOS Boot Partition only needs to be about 32 KiB in size, although in most cases make it 1 MiB because of partition alignment issues. It can be anywhere on drive and has no format.


Since the BIOS Boot Partition ("bios_grub" flag set in GNU Parted) is used without a filesystem for storing GRUB 2 boot code "unknown" filesystem! may be shown in many Partition tools.

---

### Post by OneOfMany07 on 2012-11-12
I guess now I have to figure out how to do the work after install too.  Not sure if it works when the OS is live, or if I need to boot off external media and mount the onboard drives.

I just really don't want to break what I have going :).  I guess it wouldn't be so great to have a non-bootable system if a drive dies too.

---

### Post by OneOfMany07 on 2012-11-13
I ended up testing what I already had (booting from single drives) and it booted fine without RAID'ing that tiny partition.  I just hope it works after a few updates.

---

### Post by darkod on 2012-11-13
I don't think the bios_grub "enters" inside the raid, since it's only additional space to install grub2 (part of it).
Imagine if you had the disks with msdos table. Grub2 would go fully into the MBRs so there would be no raid, right?

I recently reinstalled my home server after getting two 2TB disks and created the bios_grub on both disks because the grub2 is installed on both. But I didn't raid the partitions. I consider them simply as space for grub2.

---

