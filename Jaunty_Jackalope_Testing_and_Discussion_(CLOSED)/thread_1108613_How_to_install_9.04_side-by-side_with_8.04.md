---
title: "How to install 9.04 side-by-side with 8.04?"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MountainX on 2009-03-27
When I first installed Ubuntu about a year ago, I kept a 30 GB NTFS partition with my Windows installation. I haven't booted into that in about a year and I don't need Windows anymore.
 
Now I would like to install 9.04 beta into that partition and be able to boot either my current Ubuntu installation or the new beta. How do I do that given that I have a separate boot partition (and I'm using encryption)?
 
I would like to use the same boot partition for both 8.04 and 9.04, if possible. (I'd also like to use the same home partition, if possible, but that's a separate question.)
 
How can I install 9.04 so that it will give me the option to boot into either version of Ubuntu?

---

### Post by Chemical Imbalance on 2009-03-27
Jaunty should find the other grub settings for 8.10 automatically and include it in the Jaunty bootloader.  I just installed the beta alongside my intrepid install and it has all my grub settings.

I don't know about it working with encryption though.

---

### Post by MountainX on 2009-03-27
I'm using the alternate installer and doing manual partitioning. I'm at the point where I will select the existing boot partition (with grub for 8.04) and tell the Jaunty installer to use that (without reformatting) for its boot partition. Will this work?

---

### Post by Chemical Imbalance on 2009-03-27
> **MountainX said:**
> I'm using the alternate installer and doing manual partitioning. I'm at the point where I will select the existing boot partition (with grub for 8.04) and tell the Jaunty installer to use that (without reformatting) for its boot partition. Will this work?

I don't know if *that* will work.  I'm nearly positive that if you let it install grub to the default location that it will link to your other grub location for 8.04.
I am not positive though.

Try searching the forums for similar predicaments, bc I don't want you to hose your grub.

---

### Post by MountainX on 2009-03-27
Thank you. I decided to try it. However, at about 74% through installing the base system, the Jaunty installer thinks the CD has been removed from the drive. The CD has been checked -- it has no defects. 

I tried installing 3 times, the last time I didn't make a separate boot partition and I didn't use encryption, yet I got the same error at the same place (all 3 times). This is a separate issue, I'm sure.

The interesting thing is that after writing the partition changes earlier in the Jaunty install, the 8.04 install still boots up fine.

The Alt-F4 console shows that the installation stops just after it switches from preseed to in-target. Maybe that's a question for another thread...

---

### Post by Chemical Imbalance on 2009-03-27
Yeah, I think that's a new thread and/or a bug report for launchpad.
Hope you find a solution.

---

