---
title: "whats the best practice for dual boot?"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by wlraider70 on 2010-01-11
I'm thinking about setting up a dual boot. its currently Vista and i would add ubuntu.

i have a 750GB hard drive, ive never even passed 1/2 full.
Its my only hard disk with a main partition, and 1 small recovery partition.

I could easliy make a 100GB ubuntu partion...

or 

Could i make a small 20-50 GB for the ubuntu partition and a another for files? (is it possible use the main NTFS partition for linux files?


or

I have a spare OLD 40GB hard drive should i use that for some combination?

---

### Post by itachisxeyes on 2010-01-11
well i would make equal partitions but that is really up to you. do you for see yourself installing lots of programs on the ubuntu partition? if so go with a larger size then just 20 gigs
if you wanted to make something in the middle for both operating systems to work on i personally would format it to FAT32 simply because i have had issues with NTFS and linux before but as of late it seems to not do so bad.

i don't think you wanna play with RAID's at this point and even if you did, with that 40 gig you would at most only get 80 gigs out of it, so what you could do is install ubuntu on it and just have an ubuntu hard disk and a windows hard disk, sometimes i do that because dual booting is a bother for me

---

### Post by lindsay7 on 2010-01-11
What I would do is make three new primary partitions.Using the Ubuntu install disk with a program named Gparted or partition manager. Make the partitions around 20 gigs, 75 gigs, and 5 gigs.  When you do the ubuntu install use the manual option that you will see during the installation. Name the partitions as follows, / (this is where Ubuntu will be installed). /home (this is where you will store everything), and /swap (Ubuntu needs this to work correctly and you will not do anything with this partition). You will be asked what format you want and I would suggest that you use either ext3 or ext4. Ext4 is the new format and is said to be faster and better.

The reason you will want to do this is so that any upgrades and or reinstalls can be done to the / partition and the other two will be untouched.  It will be best to defrag your windows partition before you start to partition for the Ubuntu installation.  This make sure that all of the windows info and date is on the front of the windows partition.

You shoud do some research to confirm what I am suggesting and also see a walk thru on doing this.

[http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html](http://www.easy-ubuntu-linux.com/ubuntu-installation-606-7.html)

---

