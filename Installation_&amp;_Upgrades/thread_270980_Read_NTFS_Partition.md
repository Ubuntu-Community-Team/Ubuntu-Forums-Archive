---
title: "Read NTFS Partition"
date: 2006-10-04
forum: Installation &amp; Upgrades
---

### Post by textguru on 2006-10-04
How to read NTFS partition? Is this the easiest way ([http://ubuntuforums.org/showthread.php?t=217009)?](http://ubuntuforums.org/showthread.php?t=217009)?)

---

### Post by Jussi Kukkonen on 2006-10-04
No that's for read and write -support. It's beta, don't use it if you have important data.

wiki.ubuntu.com probably has all the options (search there), but this might be easiest:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
(edit: You just need the *Gaining Access To Other HDD Partitions* -part, the rest is again for write-support)

---

### Post by textguru on 2006-10-04
> **Jussi Kukkonen said:**
> No that's for read and write -support. It's beta, don't use it if you have important data.

wiki.ubuntu.com probably has all the options (search there), but this might be easiest:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)
(edit: You just need the *Gaining Access To Other HDD Partitions* -part, the rest is again for write-support)

Thanks for the link. Does "Gaining access to other HDD Partitions" be able to copy files to Ubuntu Disk?

---

### Post by textguru on 2006-10-04
> **textguru said:**
> Thanks for the link. Does "Gaining access to other HDD Partitions" be able to copy files to Ubuntu Disk?

Does Dynamic Disk can also be viewed on this? I have HDD that was created on Windows XP and converted from Basic Disk to Dynamic Disk. Windows cannot handle this and wanted to try if Linux can do this.

---

### Post by Jussi Kukkonen on 2006-10-05
> Thanks for the link. Does "Gaining access to other HDD Partitions" be able to copy files to Ubuntu Disk?

Yes, you'll be able to read from NTFS and copy the files to other partitions.

> Does Dynamic Disk can also be viewed on this? I have HDD that was created on Windows XP and converted from Basic Disk to Dynamic Disk. Windows cannot handle this and wanted to try if Linux can do this.
These are probably Microsoft-specific terms -- I have never heard of Dynamic and Basic disks...

---

### Post by textguru on 2006-10-05
> **Jussi Kukkonen said:**
> Yes, you'll be able to read from NTFS and copy the files to other partitions.


These are probably Microsoft-specific terms -- I have never heard of Dynamic and Basic disks...

I have already done this. On first, I cannot, its because of HDD was part of IDE controller. We have inserted HDD to USB drive and it worked! Thanks guys. Case close.:KS

---

