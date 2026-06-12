---
title: "Questions for Ubuntu 12.04 Installation (VM vs CD Install)"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by ChosenJuan on 2012-09-14
Hey guys just registered here. I would like to install Ubuntu 12.04 on my desktop, but I'm not sure whether to make a partition and install from CD, or to just use a VM (VirtualBox) to run it with Windows.

For me, the main reason I would like to try out VM is because I have multiple monitors set up so it would be nice to have Windows 7 on one monitor and Ubuntu on the other. 

I wouldn't mind making a partition on the hard drive as well, but I'm not too sure how to go about installing it on my desktop (Have Ubuntu on MacBook). Right now, I have Windows 7 installed on an SSD (60GB) along with drivers and small programs such as my browsers. Everything else (documents, games, visual studio, office, etc.) is on another mechanical hard drive. If I were to install Ubuntu on my desktop, I would prefer it on the mechanical drive. Would it still be easy to install it this way, or would I have to go out of my way and do extra steps?

I'm fine with either way, but leaning towards VM. Thanks in advance for the advice.

---

### Post by darkod on 2012-09-14
Depending what you consider easy install. :)

With two disks, and even with one, I always recommend the manual install, not using any of the auto methods. That gives you best control what goes where.
But lots of people seem not to want to hear anything about partitions and partitioning, and yet they want to install a whole new OS.

If you make unallocated space on the HDD, fire off the ubuntu install process and create all partitions you want (for example, /, /home and swap). You might find having separate /home partition useful, and for that you do need the manual install since the auto methods never create it.

VBox is also fine, at least temporarily, but it will be slower and I am not sure if all hardware will work correctly. I don't know how VBox views all hardware on behalf of the guest OS.

---

### Post by ChosenJuan on 2012-09-14
So if I were to make partitions and install Ubuntu on my mechanical drive (not ssd) it would be no different than a regular install with 1 drive? I can just boot boot the CD and make partitions/install from there?

I have installed Ubuntu a few times before, but never with a dual drive setup where I only want to use one drive.

Thanks again

---

### Post by darkod on 2012-09-14
Yeah, it doesn't care how many disks you have. Just be careful where you install the bootloader. At the manual partitioning step, under the partitions list shown there will be drop down box to select the destination of grub2.

Usually you would want to use the MBR of the same disk, like /dev/sdb for example. There should be no number in it. A number means a partition, not the MBR.

After the install finishes, go into BIOS and make sure you boot from that disk so that grub2 comes up. Otherwise the windows bootloader on the other disk will just boot windows directly.

---

### Post by ChosenJuan on 2012-09-14
Will I always have to select between which drives to boot from every time? Or after the initial setup, will it let me choose between Windows 7 or Ubuntu each time I turn it on?

---

### Post by Old_Grey_Wolf on 2012-09-14
> **ChosenJuan said:**
> 
For me, the main reason I would like to try out VM is because I have multiple monitors set up so it would be nice to have Windows 7 on one monitor and Ubuntu on the other. 

.....

I'm fine with either way, but leaning towards VM. Thanks in advance for the advice.

With a VM using VirtualBox you are running 2 operating systems at the same time. VirtualBox uses twice as much RAM and CPU as a single operating system. You must take that into consideration.

I use VMs all the time on my laptop; however, it is a quad-core with 8 GB of RAM. I have run VirtualBox on a dual-core with 4 GB of RAM;  however, it did slow down somewhat. 

It wasn't an intolerable slowness. 

VirtualBox is easy to install. After you have downloaded the iso of the distro, you can try out VirtualBox. If it doesn't work fast enough for you, you can burn an install CD or USB from the iso you downloaded then do a traditional dual boot.

---

### Post by ChosenJuan on 2012-09-14
I guess I might just try that out first then. This will mainly be used for programming (C++ for now) so hopefully VM is enough. I currently have an i5-2500k running @ 4.4Ghz with 8GB of ram so hopefully that's enough. I guess if it doesn't work out or I feel it's too sluggish, then I can do the good old dual boot.

By the way, just reiterating my question from above "Will I always have to select between which drives to boot from every time? Or after the initial setup, will it let me choose between Windows 7 or Ubuntu each time I turn it on?"

---

### Post by Old_Grey_Wolf on 2012-09-15
> **ChosenJuan said:**
> I guess I might just try that out first then. This will mainly be used for programming (C++ for now) so hopefully VM is enough. I currently have an i5-2500k running @ 4.4Ghz with 8GB of ram so hopefully that's enough. I guess if it doesn't work out or I feel it's too sluggish, then I can do the good old dual boot.

The i5 with 8 GB of RAM should work very well with VirtualBox. You can give the VM 4 GB of RAM and both operating systems should perform well.

> **ChosenJuan said:**
> By the way, just reiterating my question from above "Will I always have to select between which drives to boot from every time? Or after the initial setup, will it let me choose between Windows 7 or Ubuntu each time I turn it on?"

This only applies if you choose to dual boot. If you choose the disk where Grub2 is installed using the bios, you should be able to boot into either OS when you start up the computer.

---

