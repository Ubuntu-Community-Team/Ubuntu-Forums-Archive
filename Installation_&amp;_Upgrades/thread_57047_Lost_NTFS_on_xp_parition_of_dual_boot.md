---
title: "Lost NTFS on xp parition of dual boot"
date: 2005-08-15
forum: Installation &amp; Upgrades
---

### Post by CrakrJaky on 2005-08-15
So here's my situation, I haven't been able to find any help on after numerous searches.

I have an SATA hard drive.  First I had 2 partitions both NTFS (each taking up a 1/3 of my hard drive, the 3rd being for my future linux install).  I installed ubuntu on the 3rd partition, went thru the install did the auto setup of partitions for the free space I had leftover (the space that WASN'T ntfs)...installed grub **not** in the MBR.  Not in the mbr because I ended up having the problem with "error no os" deal. So I not have my linux up and running, but now I try to get into XP and I get the "don't have hal.dll" deal.  Yes I know there's tons of threads up about this, and I've tried to work with them except I'm having a unique experience here.  When I do the Windows install cd and go into recovery console and check out my drives with MAP I'm seeing that of my previous 2 partitions on my hard drive that were ntfs (one with windows installed on it), only one is now saying formated ntfs and the other is blank or not recognized.  The bad part here is that this is the partition to which windows is installed, so as far as I have seen, I haven't not figured out a way to expand hal.dll or better yet even read my drive.  When installing linux I never touched that partition so I'm not quite understanding whats going on here, if it's the mbr or what.  Please help! I know everything is still there on the hd but I just want to be able to access it.

Thanks ...Shaina  :???:

---

### Post by h4rdc0d3 on 2005-08-16
If I were you I'd remove the harddrive and do some diagnostics on the drive (maybe with Partition Magic) using another computer.

---

### Post by CrakrJaky on 2005-08-16
Last night I was playing around and I'm seeing that my partition w/windows on it that is supposed to be NTFS is reporting "primary boot sector invalid" Does this mean something in the partition table is amiss??? 

From what I've looked at...I've seen people trying fixboot or fixmbr from Windows recovery console, but that might ruin my partition (if it's not already) ...or getting the backup mbr and restoring that. From all that and other threads I haven't found anything that's a good idea.
thanks

---

### Post by CrakrJaky on 2005-08-18
Thank you for the advice about partition magic....I tried parition magic also to see if I could copy the partition to another ntfs drive, with no luck in that either.  I have resorted to using a data recovery program to retrieve my info (which is really all I care about doing) so now that I have that: backup time. And then I will try again to start from scratch and have still my two ntfs partitions and the third partition for linux.

---

