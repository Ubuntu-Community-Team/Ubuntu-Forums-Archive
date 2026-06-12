---
title: "WinXP partition (NTFS) refuses to resize"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by nahtical on 2006-06-03
I am using a regular x86 PC, and the appropriate version of the Dapper live CD. The CD boots up fine, and the first 4 steps of the install work, but when try to manually edit my NTFS partition windows came installed on, within a second or so it spits out an error (I dont have the exact text, but something to the effect of "Partition was unable to be resized", pretty generic). I tried editing the partition from another program (the name escapes me), but it did a similar thing. I obviously would much prefer to be able to do everything from the Ubuntu installer, or at least be able to do it for free. If it helps at all their is a second FAT32 partition for recovery (it is a Gateway laptop). Also, I defragmented and scandisked the drive with seemingly no errors. Any ideas on what could be causing problems?

---

### Post by flip314 on 2006-06-03
[QUOTE=nahtical]I am using a regular x86 PC, and the appropriate version of the Dapper live CD. The CD boots up fine, and the first 4 steps of the install work, but when try to manually edit my NTFS partition windows came installed on, within a second or so it spits out an error (I dont have the exact text, but something to the effect of "Partition was unable to be resized", pretty generic). I tried editing the partition from another program (the name escapes me), but it did a similar thing. I obviously would much prefer to be able to do everything from the Ubuntu installer, or at least be able to do it for free. If it helps at all their is a second FAT32 partition for recovery (it is a Gateway laptop). Also, I defragmented and scandisked the drive with seemingly no errors. Any ideas on what could be causing problems?[/QUOTE]

I'm not sure if the Ubuntu installer supports NTFS.  I haven't tried.  I know that QTParted can resize NTFS partitions.  It's in the Ubuntu repositories, or on the Knoppix live CD (that was how I originally resized my partitions, but that was before ubuntu, so I didn't try doing it from the ubuntu installer)

---

### Post by mjziegle on 2006-06-03
[QUOTE=nahtical]I am using a regular x86 PC, and the appropriate version of the Dapper live CD. The CD boots up fine, and the first 4 steps of the install work, but when try to manually edit my NTFS partition windows came installed on, within a second or so it spits out an error (I dont have the exact text, but something to the effect of "Partition was unable to be resized", pretty generic). I tried editing the partition from another program (the name escapes me), but it did a similar thing. I obviously would much prefer to be able to do everything from the Ubuntu installer, or at least be able to do it for free. If it helps at all their is a second FAT32 partition for recovery (it is a Gateway laptop). Also, I defragmented and scandisked the drive with seemingly no errors. Any ideas on what could be causing problems?[/QUOTE]

What partition is it?  I think you can only resize partitions located at the end of the disk.

---

### Post by nahtical on 2006-06-05
Well, I played around with GParted LiveCD some, and it turns out that NTFSresize is crashing because of bad disk sectors. 2 Windows chkdsk tests don't cough of any errors, so this confuses me slightly. GParted says I need to enable the --bad-sectors option. Is there anyway to change the options for the partitioner for Ubuntu? Or is this probably a lost cause? (A totally redo of the system would be rather impractical, as I have tons of data and programs I really don't want to have to reinstall/transfer back on to the drive).
Thanks

---

