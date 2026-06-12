---
title: "Installing with Windows 7 Problem"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by DHM100 on 2011-02-11
Wanting to install Ubuntu in Windows 7 dual boot environment.  Everything goes all right until I get to allocation.  It shows 208.1 GB for files and 108.6 GB for Ubuntu.  It would use all my hard drive space.  How do I correct this?  Also since I using the 64 bit version of Windows 7 should I install the 64 bit version of Ubuntu?  Any help would be appreciated.  Thanks!

Dean

---

### Post by Mark Phelps on 2011-02-11
BEFORE you do anything else, do the following:

1) Win7 Repair CD: Use the Win7 Backup feature to create and burn a repair CD.  You will need this later if boot problems arise from the dual-boot setup.

2) Use the Win7 Disk Management utility to shrink the Win7 OS partition to make room for Ubuntu.  Do NOT allow the Ubuntu installer to do this.  Doing that runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

When in Disk Management, take a look at the number of "drives" (that's what Win7 calls partitions) on your hard drive.  If there are four already -- you have a serious problem.  Why? Because that is the maximum number of primary partitions you can have.

If you then clear some space and force the creation of a fifth partition, you run the risk of Win7 converting your partitions to Dynamic Disks -- which is going to cause major problems for you.

---

### Post by lukeiamyourfather on 2011-02-11
> **Mark Phelps said:**
> BEFORE you do anything else, do the following:

1) Win7 Repair CD: Use the Win7 Backup feature to create and burn a repair CD.  You will need this later if boot problems arise from the dual-boot setup.

2) Use the Win7 Disk Management utility to shrink the Win7 OS partition to make room for Ubuntu.  Do NOT allow the Ubuntu installer to do this.  Doing that runs the risk of corrupting the Win7 OS partition and rendering it unbootable.

When in Disk Management, take a look at the number of "drives" (that's what Win7 calls partitions) on your hard drive.  If there are four already -- you have a serious problem.  Why? Because that is the maximum number of primary partitions you can have.

If you then clear some space and force the creation of a fifth partition, you run the risk of Win7 converting your partitions to Dynamic Disks -- which is going to cause major problems for you.

In other words backup your data first because there might be issues. If you're just curious to try Ubuntu then you could try Wubi or a virtual machine.

---

