---
title: "Triple Boot - Ub 10.04 Install Problem"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by JBoyd73 on 2011-03-27
I'm trying to install Ubuntu 10.04.1 alongside an already installed Win7+TrueCrypt and Backtrack RC2. Ubuntu says it can't find any operating systems, and wants to erase the entire disk or manually setup partitions (it doesn't see any other partitions when I select this)   

I'll go through the steps I took to get here:    

I started with a blank 640GB hard drive, formatted to 596GB, and installed Win7 from my Gateway backup disks - Windows partition used up the entire drive. I then encrypted the entire disk with TrueCrypt. After that I went into Windows disk manager and shrunk the partition by 100GB. In that new space I created a 67GB ntfs partition and left 33GB at the end unallocated. I then booted the Backtrack RC1 dvd and selected to install into the largest available free space. I confirmed afterward it was installed into the 33GB space. Lastly I booted into Windows with the TrueCrypt rescue disk to make sure everything was still there, and I deleted the 67GB partition to make it free space for Ubuntu, I rebooted into the Ubuntu CD and this is where I run into my problem.  

Any help would be greatly appreciated. Thanks, Jim.

---

### Post by billbear on 2011-03-27
Please provide the info of
sudo fdisk -lu
and 
sudo parted -l

---

