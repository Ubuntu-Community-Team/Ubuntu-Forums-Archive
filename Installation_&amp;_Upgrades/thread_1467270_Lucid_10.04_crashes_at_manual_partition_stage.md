---
title: "Lucid 10.04 crashes at manual partition stage"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by jynyl on 2010-04-30
Installing Kubuntu 10.04 Lucid AMD64 from a live CD.
During manual partition (allocating mount points to existing partitions), the installer crashes. It just vanishes and drops back to clear desktop of the live CD.

The error check from the CD boot menu reports no errors.

Running the installer from the CD boot menu (instead of running the live CD first) gives similar symptoms. At the same point in manual partitioning, the installer crashes to a black screen, then starts a live CD session of KDE.

This hardware installed the beta version of Kubuntu Lucid 10.04 AMD64 without error, and has run earlier versions of Kubuntu without this problem.

It looks like a bug to me, so posted on launchpad ...
[https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/572622](https://bugs.launchpad.net/ubuntu/+source/base-installer/+bug/572622)

---

### Post by dino99 on 2010-04-30
i always prepare the partitions with an external program like partedmagic

---

### Post by jynyl on 2010-04-30
> **dino99 said:**
> i always prepare the partitions with an external program like partedmagic
This did not involve editing partitions (no creating, deleting or resizing), just reformating one partition (for /) and allocating other existing partitions to mount points (these contain various data, to be mounted under /pub).

---

### Post by buckeyered80 on 2010-05-02
I am having the same problem with Kubuntu 10.04. The installer crashes while creating the ext4 filesystem. At first I thought this was because I have a RAID Volume, but now I see others are having the issue. If anyone has figured this out, please let us know. If I figure it out, I will post it here.

---

### Post by buckeyered80 on 2010-05-30
Actually I figured it out a long time ago and it was simple. The problem is for some reason the installer tries to configure your other partitions as well. Just make sure the partitions you are using are the only ones being assigned to swap, root, and home (if you are using home on a separate partition).

---

