---
title: "Mount problem - 6.10 EE"
date: 2007-02-24
forum: Installation &amp; Upgrades
---

### Post by daelus on 2007-02-24
I'm having a little trouble installing 6.10 on my PC.

I have a 40-gig windows XP partition I want to preserve.  I figured I'd make a 12 gig root partition, a 15 gig /home partition, an 2 gig swap file, and an 80 gig partition windows/linux could share.

I've included pictures of my partition changes in gparted, and my mounts.  As you can see, it says I haven't selected a partition to install the root, but I have.  My gparted partitions are all ext3 (except the swap, which is a linux-swap partition).

Any help would be great.

---

### Post by daelus on 2007-02-24
Solved my problem.

GParted wasn't properly creating my partitions, hence why they weren't showing correctly when I went back to take my screenshot.

I loaded up GParted separately, and created my partitions there.  It might have been due to the fact that I was trying to create my partitions at specific sizes, but I'm not sure.  Once my partitions were recognized, I was able to continue with the installation.

---

