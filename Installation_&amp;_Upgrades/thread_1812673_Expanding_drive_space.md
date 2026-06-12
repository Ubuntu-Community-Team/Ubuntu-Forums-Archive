---
title: "Expanding drive space"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by sarah8311 on 2011-07-26
Hi there.  Please forgive me as I am a complete newbie with Ubuntu and Linux.  I know Windows really well though.

My situation is that I just recently installed Ubuntu on a computer to run the FOG server for me.  This machine is Ubuntu only and there is not a Windows dual install.  I bought this machine with 2 1Terabyte drives.  Is there a way to extend the drive on to the second 1Terabyte hard drive without losing what I've already set up?

---

### Post by Mark Phelps on 2011-07-28
If what you want is to be able to treat the two physical drives as one logical drive -- you're asking to "span volumes" -- which is a RAID function.

As far as I know, there is no way (in Linux) to convert two "basic" volumes to a single "spanned" volume without losing the data.

You CAN expand existing RAID volumes (e.g., adding more drivers), but you have to start with a RAID volume.

---

