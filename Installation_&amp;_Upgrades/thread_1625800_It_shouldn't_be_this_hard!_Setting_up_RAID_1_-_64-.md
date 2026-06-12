---
title: "It shouldn't be this hard! Setting up RAID 1 - 64-bit Alternate Maverick Install"
date: 2010-11-19
forum: Installation &amp; Upgrades
---

### Post by shelzmike on 2010-11-19
Like it says in the title, I am thinking it should be this hard to install the RAID1 array in my brand new PC. Here is what is happening.

I have two brand new 1TB drives that I am attempting a new, fresh install of 10.10 on (in fact, the entire box is new). I am attempting to use the alternate desktop install so that I can have access to the manual partitioning (which is required to setup RAID 1, correct?).

I tried to use the guide here: [https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

I followed the steps, but when I got the the very end (after selecting and creating the MDs) I get an error message stating that there is no root file system defined. I went back and checked all the steps and I am sure I followed everything in the guide.

Here are some quirks (not sure if they are bugs or not) - 

In step 5 of the disc partitioning, it says to select the bootable flag and set it to yes (I am assuming). I press enter over that options, the screen flashes really quickly to a progress bar, but then comes back to the options screen and it still says bootable flag is off. No matter how many times I do it is says "off".

Also, and here is the bigger problem I think. - So the guide says to select the free space in each drive and then select Automatically Partition the free space, which I do, and it comes back and looks formatted accordingly - has 975.6 GB ext4 / and 24.6 GB swap swap. No Problem there.

BUT - whenever I do the same thing to the second drive, the partitions on the first seem to disappear. Meaning, it doesn't say free space, and has two partitions listed, but the / and the swap (last items in each row) have moved to the second drive partitions. I am not sure if this is how it is supposed to be since the pictures in the linked guide to not show what it looks like after that.

THis is driving me crazy and I have to have it set up in RAID 1 and unsure as to what it is I am missing. Thanks.

Mike

---

### Post by shelzmike on 2010-11-19
Okay, here is what I figured out:

1.) I was able to rectify the / and the swap disappearing on the first drive that is formatted when the second one is formatted by simply using the "create partition" manually option.

2.) The walkthru misses a step that makes a huge difference which was causing my "No Root File System" error. That is, you have to go into each partition of the RAID and mark it for its use (i.e. ext4 and swap). That did the trick.

Mike

---

