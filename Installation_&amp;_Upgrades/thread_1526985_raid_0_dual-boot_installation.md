---
title: "raid 0 dual-boot installation"
date: 2010-07-08
forum: Installation &amp; Upgrades
---

### Post by hej.mich on 2010-07-08
What is the best way to install Windows and Linux on two-hard-disk array?
In fakeraid there are no problems in Win, but linux installation is almost impossible (i've tried unsuccessfully...).
In software raid it would be impossible to share files between win and linux?
And finally hardware raid is possible, but cheap controllers have low performance....

Is there any other way (apart from spending a lot of $$ for adaptec controller) ?

---

### Post by ronparent on 2010-07-08
You don't say which version of Ubuntu you are trying to use. There is a different guide for each version. Since windows is on your array it appears that your bios setting are correct. 

In 10.04 it is actually relatively easy. You have to use gparted in a live cd session of version 9.04 or earlier to create all of the needed target partitions on the raid array (/, swap, /home, etc.). Also if you are planning to boot from the array, in step 8 of the install you have to select the advanced box and then select the entire array (not a raid partition) in the drop down box as the location to install the grub bootloader. If you attempt to format any partition during the install the install will fail. If you try to install the grub boot loader to a disk (sda , sdb, etc.) the install will fail. 

For any version prior to 10.04 goggle the topic 'installing to fakeraid'.

---

