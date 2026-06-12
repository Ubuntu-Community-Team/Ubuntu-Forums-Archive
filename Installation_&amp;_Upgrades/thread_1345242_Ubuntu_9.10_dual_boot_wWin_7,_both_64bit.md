---
title: "Ubuntu 9.10 dual boot w/Win 7, both 64bit"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by cjwescott on 2009-12-03
I installed W7 64bit  (new computer build). 1tb drive divided into 4 partitions.

I then shrunk the C partition by 75gb.

I then reboot to install Ubunto off the live CD.

When I get to the paritioning area (Prepare Partitioning) of the install  I see the 75gb of free space except further below is states that that space is unusable and there are no options other than the Revert button to choice from when highlighted.

What is happening here?

Should I be doing this another way?

I have tried this over and over again various ways with zero success at getting Ubuntu installed.

Chris

---

### Post by phillw on 2009-12-03
> **cjwescott said:**
> I installed W7 64bit  (new computer build). 1tb drive divided into 4 partitions.

I then shrunk the C partition by 75gb.

I then reboot to install Ubunto off the live CD.

When I get to the paritioning area (Prepare Partitioning) of the install  I see the 75gb of free space except further below is states that that space is unusable and there are no options other than the Revert button to choice from when highlighted.

What is happening here?

Should I be doing this another way?

I have tried this over and over again various ways with zero success at getting Ubuntu installed.

Chris

Hi,

if you can see the partition from Win, delete it. That will set it to 'un-allocated' and Ubuntu will ask you to install on the unallocated area.

Phill.

---

### Post by cjwescott on 2009-12-03
Thanks for the reply.

I ended up trying my original method which was to install W7 and leave a portion of the drive unallocated, but this time I only made _three_ partitions + an unallocated space.

This time when I ran Ubuntu for install it allowed me to install on the unallocated space.  I guess it was that I had created _four_ partitions + unallocated space the first time which prevented Ubuntu from installing on the unallocated space.  

Boy I could have saved to nights of aggravation if I new this ahead of time!:oops:

Chris

---

### Post by presence1960 on 2009-12-03
> **cjwescott said:**
> I installed W7 64bit  (new computer build). 1tb drive divided into 4 partitions.

I then shrunk the C partition by 75gb.

I then reboot to install Ubunto off the live CD.

When I get to the paritioning area (Prepare Partitioning) of the install  I see the 75gb of free space except further below is states that that space is unusable and there are no options other than the Revert button to choice from when highlighted.

What is happening here?

Should I be doing this another way?

I have tried this over and over again various ways with zero success at getting Ubuntu installed.

Chris
There is a four primary partition limit on a hard disk. Either four primary partitions OR 3 primary and 1 extended partition. Within the extended partition you can make as many logical partitions as you desire. The only constraint on that is how much space you have allotted to the extended partition.

[https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics](https://help.ubuntu.com/community/HowtoPartition/PartitioningBasics)

---

