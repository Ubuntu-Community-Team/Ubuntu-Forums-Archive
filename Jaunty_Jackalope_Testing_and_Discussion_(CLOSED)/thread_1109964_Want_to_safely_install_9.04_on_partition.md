---
title: "Want to safely install 9.04 on partition"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by JGreenidge on 2009-03-29
Greetings:

I have a 1.25 eMac and 320gig LaCie drive with six partitions, one partition originally set up in UNIX format via Disk Utility. I have Jaunty 9.04 up and going through the installation menu but don't want to proceed until I'm sure. On Disk Utility on my Mac, the UNIX disk is identified as disk1s9, as it is sda9 on the Ubuntu installer screen as well. How should this partition be formatted? New World or FAT32 or the various journal ones? What "point"? I'm no techie, just steady by the book, so I'd appreciate any step-by-step guidance if possible. I'm anxious to see Ubuntu up and running on this thing!

Thanks!

Jim

---

### Post by pbpersson on 2009-03-29
I would go with EXT3 and make sure you do manual paritioning and it is ONLY touching the partition you want it to.

You will also want a swap partition somewhere

The main mount point - the only one you REALLY need is called "/"

Everything else will go into there if that is the only one you specify

---

### Post by JGreenidge on 2009-03-29
> **pbpersson said:**
> I would go with EXT3 and make sure you do manual paritioning and it is ONLY touching the partition you want it to.

You will also want a swap partition somewhere

The main mount point - the only one you REALLY need is called "/"

Everything else will go into there if that is the only one you specify

Thanks for the SWIFT reply!
Okay, I see where you are. I didn't realize I needed another ("swap") partition too, tho. Does this mean if you formatted your Mac with just two partitions with Tiger on them that you'd have to reformat the drive into three partitions for Ubuntu, its "swap" partition and your regular Tiger partition instead of just having one Tiger and the other Ubuntu? Wish there was a way to resize partitions already there too, though I guess that's a whole different topic. Anyway, I'll reap all your feedback till I commit later on. Thanks!

Jim

---

### Post by cyberdork33 on 2009-03-29
I think you can resize your HFS+ partitions with gparted. (well, shrink anyway)

---

### Post by JGreenidge on 2009-03-30
Well, looks like I've been checkmated. Right on the end of the Ubuntu installation a window pops saying that it has to delete the installed operating system files on the disk first so to proceed, and since I'm using a partitioned disk with Tiger on one partition, I'm afraid that means it's going to erase all traces of OS-X so to install Ubuntu. Am I wrong? Can Jaunty really be installed on a partitioned disk alongside Tiger or it needs the whole sheebang? Any hints would be appreciated! Thanks!

Jim

---

### Post by JGreenidge on 2009-03-30
Before I take the plunge/risk of installing Jaunty on my main LaCie HD, I'm using it on my old G3 900mHz iBook. Runs well, and I had to create two partitions to make it go. So far two creavats; Power management seems to keep the HD spinning without idle and so turns the fan on continuously, which it rarely ever did under Tiger. Also there's no way to adjust screen brightness via the F-keys, though audio ones function well. More to come.

Jim

---

