---
title: "No install love, Dapper doesn't see my sata drives"
date: 2006-06-22
forum: Installation &amp; Upgrades
---

### Post by ddales on 2006-06-22
Hi, I posted before and then found a couple of postings that I thought might help.  It turns out that didn't work either.

**Situation**
Long time Suse user and I'm pretty happy with 10.1 but wanted to see what all the fuss about Dapper was.  I thought I would try it, but I can't.

**Problem**
Ubuntu can't seem to recognize my hard drives.  I've tried the live DVD and the install a couple of different ways now but it just doesn't see my hard drives.  One solution that I saw was to start the live, go to System - Administration - Gpart and partition my drives there.  Then start the installation from the installation icon.  No love.  No devices detected.

**Hardware**
Dell 9150  (no cracks, I love Dell)
P4 3.4Ghz HT650 64bit
2Gb memory
Nvidia 6800 256Mb
2 x Western Digital 160Gb SATA 150

**Goal**
Get Dapper installed and give it a go to see if I really want to switch from OpenSuse.

**Notes**
I've never used *buntu of any kind but would really like to check it out.  I'm a *buntu noob but know my way around linux very well.  I assume ubuntu doesn't have the raid drivers for my motherboard and therefore can't see my hard drives.  I would find that highly unlikely though.

Thank you in advance for any suggestions!  BTW, it's AMD/EMT 64bit

---

### Post by wpshooter on 2006-06-22
2 things.

Are you trying to install using the RELEASED version of Dapper ?

Have you tried disabling the second SATA drive and seeing if Dapper will recognize and install to the one drive remaining active in the system ?

---

### Post by ddales on 2006-06-22
Yes, it is the released version!

Ok, after several hours of trying different things, I have come to the conclusion that Dapper sucks!

I changed my hardware raid options in the bios and dapper now can see my drives.  However, there is no opportunity whatsoever to use RAID 0 (stripe) and have dapper see it as such.  The partitioner always sees each drive seperately.

After some more hunting, I caught wind of some Dapper Alternate CD?  This will supposedly allow you to arrange your partitions with LVM.  (stripes)

For an OS that has a Linux Marketing Tool of {It Just Works} is hilarious!

Goodbye Ubuntu, Hello Opensuse!!!!!

---

### Post by wpshooter on 2006-06-22
[QUOTE=ddales]Yes, it is the released version!

Ok, after several hours of trying different things, I have come to the conclusion that Dapper sucks!

I changed my hardware raid options in the bios and dapper now can see my drives.  However, there is no opportunity whatsoever to use RAID 0 (stripe) and have dapper see it as such.  The partitioner always sees each drive seperately.

After some more hunting, I caught wind of some Dapper Alternate CD?  This will supposedly allow you to arrange your partitions with LVM.  (stripes)

For an OS that has a Linux Marketing Tool of {It Just Works} is hilarious!

Goodbye Ubuntu, Hello Opensuse!!!!![/QUOTE]

Did you **try** the alternate CD ?

If you decide on Suse, I hope you have better luck with it than I had.  I could not ever get it to do such a simple thing as configure and print a test page to my HP2100 laser printer.

Good luck.

---

