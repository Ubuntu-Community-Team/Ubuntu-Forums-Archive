---
title: "Replacing Ubuntu 10.04 with Lubuntu 12.04 in a dual boot machine"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2012-05-03
This may be a stupid question but I cannot find the answer any where.  I have an ASUS EeePC 1000H that has two OS installed.  On sda1 I have Ubuntu 10.04 and on sda2 (which is an extended partition) I have Lubuntu 11.10 plus the swap partitions.  What I want to do is replace the Ubuntu 10.04 on sda1 with Lubuntu 12.04 and I understand that all I need to do is delete what is on there and then later install to the unallocated space.  My question is  Since Grub is installed on the primary partition (sda1) is that going to bonk everything?  Do I need to do something else?  I had kept 10.04 on the primary and used the other half of the drive to install other Operation Systems.  I had Mint, Lubuntu 10.10, Lubuntu, 11.04, and Lubuntu 11.10 on it at one time or another.  The question never came up because Grub is on the other partition.  Do I have a problem?

---

### Post by mips on 2012-05-03
> **Rex Bouwense said:**
> 
sda GRUB2
sda1 Ubuntu 10.04 ----> Lubuntu 12.04
sda2 Lubuntu 11.10  

What I want to do is replace the Ubuntu 10.04 on sda1 with Lubuntu 12.04 and I understand that all I need to do is delete what is on there and then later install to the unallocated space.  My question is  Since Grub is installed on the primary partition (sda1) is that going to bonk everything?

Start up the install media, I'm assuming you use a USB flash stick, when it comes to partitioning select manual partitioning and tell the installer to use **sda1** and to format it. When/if it asks about GRUB specify it installs to **sda**, it will install to sda and update its menu with Lubuntu 11.10 on sda2 as well.

This is assuming nothing goes wrong but this is how it should work.

---

