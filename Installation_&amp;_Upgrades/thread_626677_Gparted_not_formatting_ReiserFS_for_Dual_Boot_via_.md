---
title: "Gparted not formatting ReiserFS for Dual Boot via EasyBCD"
date: 2007-11-29
forum: Installation &amp; Upgrades
---

### Post by Paradoxfox93 on 2007-11-29
So I saw this guy's recommendations for using EasyBCD and decided to give it a shot cuz it looked simple enough and I'm trying to get Vista on my CPU so I can play Starcaft (Wine ain't working for it).  The problem with this is that the linux live CD won't partition the way they're specifying. Moreover, the pictorial is lacking significant amounts of information. Like: How big do I make the Grub Partition? (Which I found the answer to - 1mb) Or, If I'm labeling the Grub partition "/" what do I label the root partition where I'm installing Linux to get the installation to recognize THAT partition as the target of installation? (I kinda took a stab at some combos you can see below...none of which worked though that may not be the issue).

More to the point though, When I try to set things up like that I can never even install ubuntu because gparted can't format the drive like that. I've tried to arrange them into several orders. I've partitioned with Gparted and with Vista (Most success with Vista, still no Formating by Gparted though). It will always tell me that it had an error trying to format the ReiserFS space, then the installation goes back to partitioning, and the reiserFS space is labeled as Swap. I cut it up so that the Reiser FS was the first partition with Vista. Before that I was using Gparted and tried quite a few combonations to no avail. Any ideas? reccomendations
Current Non-working Combo:
dev/hda1 - ReiserFS - "/" or "/media/hda1" - Format (Checked) - (2mb)
dev/hda2 - Swap - (1024mb)
dev/hda3 - ext3 "/" or /media/hda3" - Format (checked) -120gb)
--------
dev/hda4 - NTFS - Vista - 36gigs


What am I missing? any ideas?

---

### Post by Computer Guru on 2007-11-30
I replied to your PM - basically, you need only two partitions for Linux: a / and a swap.

/ needs to be bigger than 2mb.

---

