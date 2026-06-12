---
title: "Installation Partition Problems"
date: 2008-08-14
forum: Installation &amp; Upgrades
---

### Post by hamishhamishhamish on 2008-08-14
okay, so I've been using ubuntu (8.04) as a live cd for a couple of days now and I love it, so i've decided to install it as a dual boot.
The only problem is that when i'm trying to install it- it gets to the stage about partitioning and there is only 2 options, guilded (use entire disk) and Manual, unlike the tutorials i have seen online which have 4 options.
I still want vista so i'm not going to use the entire disk and the manual mode is a little too advanced for my liking.
Oh and i'm running windows vista home premium with 1GB of ram and an intel pentium dual core T2130 with 160GB hardrive which came already partitioned into C:/ (labelled OS) and D:/ (labelled recovery)

Thanks in advance

---

### Post by pastalavista on 2008-08-14
So your problem is, "the manual mode is a little too advanced for my liking." If you had any specific questions, it would be much easier to help you. I thought it was pretty simple the first time. All you need to do is tell it how much space you want Ubuntu to use on the disk (don't forget the swap partition.. about a gig should do it) and it will automatically shrink the Windows partition enough to accomodate it. If you're so nervous about messing up, just be sure to backup your Windows drive first.

---

### Post by hamishhamishhamish on 2008-08-14
sorry :S its quite hard to explain 
the problem is that when I'm installing it i only have the options to create a partition manually or to go over the entire hardrive, instead of the 4 options i should have like the online tutorials have.
So i'm wondering how to get the other options so that i can easily create a linux partition.

---

### Post by Pumalite on 2008-08-14
You have to allocate space for Ubuntu with the Vista Partitioner first. Then install; go Manual and create 3 'New' partitions in the 'free space':
10 GB for '/'
The rest minus the amont opf RAM for /home
The amount of RAM for /swap

---

### Post by hamishhamishhamish on 2008-08-14
okay
I decided to just install it inside windows

this thread can die now

---

