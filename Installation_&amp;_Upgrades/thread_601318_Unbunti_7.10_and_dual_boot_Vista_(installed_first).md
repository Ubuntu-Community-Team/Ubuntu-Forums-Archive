---
title: "Unbunti 7.10 and dual boot Vista (installed first)"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by Galaxian on 2007-11-03
Earlier this week I posted the following:

>>I have installed Ubuntu on a separate hard drive. I shrunk the existing partition to make room and installed on the 'unallocated space' using the manual method.

>>I made sure that 3 partitions were set up; two ext & swap. This included /boot so I thought Grub would not affect my Vista installation, however my MBR was trashed but I fixed that (got an error 22 when booting). I set all three as primary partitions although I am not sure if this was correct (I now have more than 4 primary partitions but Vista does not see the Ubuntu partitions except under the Computer Management console.

>>I thought that I could install Ubuntu completely separately and manage the dual boot in Vista by using EasyBCD 1.7. I' ve added a Linux entry and pointed to the /boot partition but am having no joy. I guess Grub needs setting up again but am reluctant to attempt from the LiveCD given my previous experience.

>>I have followed the instructions in the following thread: [http://ubuntuforums.org/showthread.p...highlight=grub](http://ubuntuforums.org/showthread.p...highlight=grub)

>>When attempting to find grub I get a code 15 error: file not found. Now I'm sure that I've installed Ubuntu. However, when I look at the 3 partitions set up on the manual install through Vista I notice that there is no file system and no drive letters have been assigned. I can only seem to delete the volume within computer management - no drive letter can be assigned.

>>I've loaded the live cd and Unbuntu cannot see the partitions either so I wonder whether this is the reason I'm having problems.

>>I have one more question for now: if I manage reinstall grub on the correct partition (/boot?) will this erase the rest of the physical drive (which has 5 partitions inc 3 reserved for Ubuntu)?

I started again following the instructions at [http://www.howtoforge.com/dual_boot_...ntu_feisty_p2?](http://www.howtoforge.com/dual_boot_...ntu_feisty_p2?) to the letter. This time I noticed that I was instructed to set two partitions up: excluding /boot. Installation again went fine but again when booting up I get an error 22!!!!!!

Unfortunately, I am at the point of giving up!

Please help!

All I want is to run Ubuntu from a separate physical drive!

---

