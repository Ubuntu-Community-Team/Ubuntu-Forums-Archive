---
title: "Dual Boot Partitioning problems during Install"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by linuxa on 2006-06-04
Hi all

I'm having my first go at install Kubunut 6.06 :mrgreen: 

The LIVE Session looked pretty good, so I went ahead with Install.

However was halted at the partitioning phase. Here's what happened.

I have an 80GB Harddrive that I'm wanting to partition half-half with Windows & Kubuntu. With the extra requirement of having a separate** /home** partition so I don't lose data when I feel the need to reinstall.

So I'm at the partitioning screen where the resizing went smoothly, and I'm trying to partition what I have left of the 40GB.

Imagine my surprise when I find that no matter how I do it, I am always left with 2.58MB of free space that exists on a Primary Partition of its own. I've tried resizing my Windows Partition just to be sure that 40GB for the first Primary Partition isn't the cause of this weird error. What happened next is that the size of the slice of free space changes (and not in a predictable manner either), but it's always there. Taking up one of the 4 Primary Partition slots that I could create on the harddrive.

Now normally I wouldn't mind having 2.58MB wasted on a harddrive of this size, and I could always create Logical Partitions out of **/**, **swap**, and** /home.** 

The problem is however compounded by the fact that the next stage of the  installation (the one before the Installation confirmation) forces me to choose 2 mount points (or more), one for /, and one for swap, with the only possibilities being Logical Partitions (?!).

In other words:

  4 Primary Partitions in Total
- 1 (2.58MB free space) Partition
- 1 Primary Partition for **/**
- 1 Primary Partition (I can't pick Logical) Partition for **swap**
= 0 Primary Parition for **/home**

I'm at my wits end with regard to the following questions:
1) Why is a hidden Primary partition slipped in during repartitioning?
2) Why can't I choose Logical Partitions as mount points?

Just one more piece of info, I've been looking at the step-by-step guide for install Ubuntu 6.06 at the following site:
[http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

As well as being very useful, it shows that when installing Ubuntu (which uses GParted as opposed to QtParted used by Kubuntu), partitioning with Windows on the harddrive doesn't generate a hidden partition (for (1)). And Logical Partitions can be used as mount points (for (2)).

I did downlad GParted and found that it was also creating a hidden Primary Partition. So the idea that I could pre-partition my hd before installation seems to be out of the question now.

If anyone has any info regarding their own experiences at partitioning for Dual Booting with Kubuntu, I'd appreciate it greatly if you could post.

Thanks in advance
Linuxa

EDIT: Issue (2) seems to be a bug in the Installer which wasn't updating the Mount Point Selection Screen if one were to go back to the partitioning screen (one step earlier) and changed the harddrive layout. 

So basically I created a couple of Primary Partitions to begin with, went onto Mount Point Selection, found that I had left out a partition or two, went back, repartitioned. The Mount Point Selection screen still had the old harddrive layout from the first partition. Workround is exit & restart Installation after the new partition plan has been committed.

---

