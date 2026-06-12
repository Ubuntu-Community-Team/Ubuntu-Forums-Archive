---
title: "Migrating 10.10 to a new local HDD"
date: 2011-04-15
forum: Installation &amp; Upgrades
---

### Post by Suff0c8r on 2011-04-15
Hey all! Mandatory note about how I LOVE Ubuntu and really, really loathe Windows (I find it feels really closed and hostile, but thats me).

I have 3 SATA hard drives, one 500GB NTFS with Windows, one 320GB With Linux (one partition)and one newly purchased 1TB.

The 500GB has Windows, which I use to LAN and do graphic stuff while I set up Wine. Its got 1GB free space.

The 320 I found in my garage, and is on it last leg, often not showing as boot or displaying as "Bzbzbzbzbzbzbzbzbzb  bzbzbzbzb" (No lies). As I was low on space already, i decided to by a 1TB, move Ubuntu across and go from there.

The Issue:How would I copy my system from one HDD to the other, and also add a 500GB NTFS partition. What is the ideal way to set up the partitions, and how big should my swap be? I looked for partitioning guides but they're all REALLY outdated (one suggested a whole 128mb swap)

Sorry if this is a n00b q and meant for the beginner section...I'm unsure of where it stands. Any help would be hugely valued! And if my posting etiquette is off, I'm open for correction :) 

Thanks in Advance!!

---

### Post by Blasphemist on 2011-04-15
It may or may not be a good idea to migrate from a bad hard disk to a good one but that is your decision. At least I understand from your post that the bad drive is where Ubuntu lives. It could be a backup of home, install Ubuntu new on the new disk and copy back of what you want back from the home backup is cleaner.

I think you should use the GParted manual to plan this. I am attaching the page on copying and pasting an unmounted partition. You'll need a Ubuntu live CD or gparted live cd or a system rescue cd so that you can have the Ubuntu existing partition unmounted. 

I believe Clonzilla would be an option to use but I haven't used that.

---

### Post by Suff0c8r on 2011-04-16
Sorry, I thought my message had posted, but Chromium hung and it never got through. 

Ubuntu is indeed on the faulty HDD.  I want to know if copying the home folder will take all my programs and settings across, or JUST the settings? I have a few gig's worth of updates i do NOT want to download again. Thank you so much for your reply!!

---

