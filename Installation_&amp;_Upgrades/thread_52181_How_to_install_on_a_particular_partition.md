---
title: "How to install on a particular partition"
date: 2005-07-26
forum: Installation &amp; Upgrades
---

### Post by 6dof on 2005-07-26
First time post and relatively new to Linux (and Ubunto).

I currently have WXP Pro and WXP64 set up in a dual boot configuration.  I've created a blank 10GB partition to load the 64bit version of Ubunto 5.04.  I have the install CD from Ubunto.  How do I intall Ubunto on the empty partition?

The empty partition is the 4th on the drive and is not formatted.  I'd also like to install GRUB to handle booting to the different OS's.

Should I use the default or expert install?  Then what should I do?

TIA for any help you have to offer,
Doug

---

### Post by jpincheira on 2005-07-26
well, in the Ubuntu Installator you have to select the partition, do an <enter> and select a filesystem (it can be ext3) and mount it to: "/". but you have a problem, you need a swap partition, so, if you don't have more space try to do a 9,5 gb ext3 "/" partition and use the rest of space on a 0,5 gb swap partition. For swap you have to do the double of your pc ram, for example, if you have 256 ram you've to do a 512 mbs swap partition.

---

### Post by 6dof on 2005-07-26
Well, I should have read the installation notes on the CD before posting to the forum.  Sorry about that.

I did try the default install and got to the point where it asked for partitioning the whole drive or manually partitioning.

The problem that I ran into is my laptop has hardware RAID0 through a Promise controller.  Is this a show stopper?

The Ubuntu installer simply showed my 2 HD's without any partition data.

When installing WXP, I had to install some drivers at the beginning of the installation to get XP to recognize my drive set up (F6 to install special drivers...).  Is there something similar to this for Linux/Ubuntu?

TIA

---

### Post by 6dof on 2005-07-26
I should mention that the Live CD loads and runs fine.

---

