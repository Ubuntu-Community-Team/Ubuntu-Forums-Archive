---
title: "Gparted - Disk label"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by interphantom on 2006-08-21
Ok, I screwed up last night.  It was late and I wasn't paying attention when I ran gparted.  Basically, I have 2 serial drives running raid 0 with XP on it.  I have an IDE drive that was going to run Linux.  When gparted came up, I hit create new and gave it a new label; gave it a MSDOS label.  Well, it was right after I hit "Sure, go ahead... I know it'll get deleted and it's fine" that I realized I had selected the first of my two serial drives.  So I'm racking my brain trying to figure out how I can get that drive back.  It hasn't been formatted, so the data is all still there but I can't get to it.  Since it is in raid, I've lost everything... which I really need back.  So am I up a creek without a paddle?  Please if anyone can think of anyway to get that drive back, I'd have your baby.

---

### Post by wpshooter on 2006-08-21
1) I hope you have some backups.

2) Might want to try downloading a free or perhaps think about purchasing a good hard drive recovery program.

3) I wish you good luck, but I am sort of afraid that we are not going to be parents together.

---

### Post by interphantom on 2006-08-21
1) No backups

2) Raid configured drives... doubt I can use a data recovery program

3)I was going to name him Frank :(

---

### Post by moeFinley on 2006-12-05
I guess it's a bit late now but normal Check Disk (Chkdsk) in DOS would have fixed that.  If you boot from your WindowsXP/98/95 Check Disk is in the RAM drive.

---

### Post by wpshooter on 2006-12-05
You could possibly be correct, but I sort of have my doubts.  I believe that when you give the drive a new label, that you have wiped out the entire structure of the drive including the FAT tables and the partitioning information.  I don't think the chkdsk utility will recover any disk information without access to the partitioning and FAT table info.

But worth a shot.

And if it works, I hope you are ready to be a dad, moeFinley !!!

---

### Post by moeFinley on 2006-12-09
I've had drives that were unreadable in anything because the partition is screwed and simply running Chkdisc has got the drive back to normal.

I don't know if it needs the disk label intact but I don't see why it could re-create it?

I'm no expert though and I stand to be corrected.

---

