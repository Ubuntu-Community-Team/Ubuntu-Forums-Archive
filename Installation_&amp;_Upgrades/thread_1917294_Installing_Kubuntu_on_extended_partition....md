---
title: "Installing Kubuntu on extended partition..."
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by leonardodag on 2012-01-29
I'm willing to install Kubuntu alongside Windows, on a separate partition. I'd like to know if I can install it on an extended partition, because my disk already has 3 partitions (seems that it's common on Dell PC's), as follows:

Partition 1: <no label>, 39 MB, <no filesystem appears on Windows Disk Management>
Partition 2: RECOVERY, 14,65 GB, NTFS
Partition 3: OS, 283,40GB, NTFS

I want to shrink the OS partition, and create these three logical partitions: the root partition, /home and a swap partition.

On some sources I've seen that it's not possible to boot from a logical partition, but on others I've read that all linux partitions can be logical. Can I do it or not?

Also, someone knows what the unlabeled 39MB partition does?

---

### Post by mikewhatever on 2012-01-29
Yes, all Linux partitions can be logical. It's Windows that can't boot when installed on a logical partition.

---

### Post by leonardodag on 2012-01-29
Thanks.
If someone knows what the 39MB partition is, i'd like to know :) (why the heck didn't dell merge it with the recovery partition or something like that? do they really need another partition?)

---

### Post by mastablasta on 2012-01-30
i think it's boot partition, but this is more a quesiton for windows forums.

---

### Post by SeijiSensei on 2012-01-30
Sometimes Dell puts a set of custom diagnostic programs in that first partition.  At 39 MB that sounds plausible.  Since I usually build Linux-only machines I generally blow away everything on the drive and start from scratch.  I've never missed whatever Dell puts in that partition.

If the "recovery" partition contains the optical disk images to make a set of Windows recovery disks, I'd run the program to burn the images, then start over with a clean disk.  

Be glad you don't own an HP where all four primary partitions are in use from the factory.  Installing Ubuntu as a dual-boot in that situation takes a lot of work.  Maybe some of my [experiences with an HP]("http://ubuntuforums.org/showpost.php?p=11299287&postcount=5") can give you some ideas.

---

### Post by leonardodag on 2012-01-30
I was thinking about doing that... My computer should have shipped with a 500GB hard disk, but came with what seems to be 300GB, so I'd like to use these 15 GB of the RECOVERY partition.
My computer shipped with a recovery cd, so I don't think I need the partition... I'll do the backup anyway :)

---

### Post by SeijiSensei on 2012-01-30
Does the BIOS report the drive as 300 GB?  I'm sure Dell must make mistakes sometimes, but I've never gotten a machine from them with a smaller drive than I ordered.  If the BIOS thinks it's 500 GB, I'd boot from an Ubuntu CD, open a terminal, and run "sudo fdisk /dev/sda" and see how it looks to Linux.  Maybe there's just a big chunk of unpartitioned space.

---

