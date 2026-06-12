---
title: "RAID 0 Install + grub"
date: 2005-09-19
forum: Installation &amp; Upgrades
---

### Post by eeyoredragon on 2005-09-19
I have two 74GB SATA raptor drives that I'd like to install ubuntu to in RAID 0. Following the instructions from elsewhere in the forums, I have done this:

disk1
1.0GB /boot ext3 (have tried ext2)
rest RAID space

disk2
1.0GB swap
rest RAID space

then I set up RAID. Choose RAID0. Select the only two active devices that show up in the list (which I assume are the two equal sections set aside for RIAD as stated above). Write info.

Now I see a new RAID device with the sum of the RAID spaces. I select that, format it as ext3, mount point / (root). Finish partitioning.

Install automatically. When it reboots, GRUB hangs after "Please wait..."

I've tried LILO with the expert install ^ doing that and LILO won't even install. It reports "Error1". GRUB will install, but hangs as before on restart.

I have the hardware RAID controller disabled. Am I doing something stupid?

---

### Post by tonysathre on 2005-09-19
why do u have RAID diabled when u want to use RAID, are u using software RAID instead?

---

