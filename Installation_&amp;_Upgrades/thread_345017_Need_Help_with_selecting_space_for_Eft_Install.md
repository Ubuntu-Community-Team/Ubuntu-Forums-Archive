---
title: "Need Help with selecting space for Eft Install"
date: 2007-01-23
forum: Installation &amp; Upgrades
---

### Post by Goober on 2007-01-23
I am attempting to install Edgy Eft, and having some issues with it.  I just had Windows encounter a major error of some sort, and I finally decided to switch back to using Linux.  I have installed Linux before, Breezy and Hoary, and managed to figure out the partitioning with those systems, but I am having troubles figuring out how to select the partition I want with Edgy`s install program, Step 5 out of 6.

I have 3 partitions on my Hard drive, 2 should be NTFS, which Edgy is not recognizing, and one is ext3, which is where I want to install Edgy.  Edgy is not recognizing the 2 NTFS partitions, it sees it as ùnallocated`space. Edgy provides 3 options on Step 5, one to erase the entire disk, which I dont want to do because there are files on the NTFS I want to try and salvage, one to use the largest continuous free space, which Edgy sees as the NTFS partitions, which I dont want to do because that would be the NTFS partitions (Which Edgy recognizes as one large partition), and the last option is to manually edit the partition tables, which sounds like what I want to do.

When I select the last option to manually edit the partition tables, and select the ext3 partition I have, this is where I get confused.  It tells me I need to make 2 partitions, one a Slash and another Slash home or something. (My keyboard is not totally working with Edgy yet, I cant type in the slashes, apostrophe, commas, etc ... )  My question is how do I make those partitions (Question Mark)  And how do I do what I want to do, which is to install Edgy on the ext3 partition, and leave the NTFS ones alone (Question Mark)

Thanks in advance for your help.

---

### Post by mandrakethepenguin on 2007-01-23
I recommend using the alternate install CD, assuming you're using the desktop installer, the partition editor and keyboard map detector are much more powerful.

---

### Post by Goober on 2007-01-23
Just to close this issue, I managed to figure out what I was supposed to do, apparently I needed to make a little swap partition - whatever that is.   I made it a Gig, which seemed about right.

So ... ya ... I`ve figured out my problem ...

---

