---
title: "Need for comfort: Hardy Heron"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by b1lancer on 2009-12-14
Hello,

I've been doing as much reading as I can (shaking of this things called 'noob' possible?). I'm am really willing to work with 9.10. However, I've got a lot of important files and I need something absolutely solid. I've used Hardy Heron before and it was what got me into Ubuntu in the first place. 

I would like thoughts on how to upgrade open office in hardy heron (tried that before and failed miserably) and which updates do I look out for?

Thanks.

---

### Post by mikewhatever on 2009-12-14
If you don't want to loose your important files, no matter what OS you run, make regular backups. Both Hardy and Karmic are good releases, that said, both have bugs, so I think it doesn't really matter which you use.

---

### Post by fancypiper on 2009-12-14
Keeping my data intact with distro hopping/upgrading/re-installing is the reason I chose my partitioning scheme using a minimum of 3 partitions:

/
swap
/home

I just choose the manual partitioning if I swap distros or re-install and choose to **not** format my /home partition (and my other data partitions)

When I choose to swap distros/reinstall, all my data is there with no problems.

---

### Post by b1lancer on 2009-12-14
Well, there is this thing ubuntu one, but from what I'm reading, it's got it's quirks still. 

How do you create that separate partition? And how do you keep it from being erased?

another idea I had was getting another internal hard drive... but what would i have to do so I can write files to it from inside ubuntu, without installing it? Kind of like a massive usb drive.

i could get a usb harddrive, but I want to keep my cost down... and learn about this stuff along the way.

---

### Post by audiomick on 2009-12-14
> **b1lancer said:**
> Well, there is this thing ubuntu one, but from what I'm reading, it's got it's quirks still. 
Ubuntu one is very new. It is probably pretty good already, but I would not consider using it for critical backups.

> How do you create that separate partition? And how do you keep it from being erased?
You can create partitions using gparted, which is installed on the live cd and can be installed on an installed Ubuntu via Synaptic package manager

> another idea I had was getting another internal hard drive... but what would i have to do so I can write files to it from inside ubuntu, without installing it? Kind of like a massive usb drive.

i could get a usb harddrive, but I want to keep my cost down... and learn about this stuff along the way.

An internal drive is likely to be much easier to deal with than a usb drive. I have seen lots of posts from people having problems with usb drives.

To write files to it, you have to create a partition, or several, on it with a linux file system (ext3 or ext 4, for instance) and mount it.

I would suggest the following:

**_back up your important files to somewhere outside your computer. External drive, DVD or whatever_**

get a live cd for 9.10, boot from it using the option "try ubuntu without changing the computer", and see if everything works on your computer. Let's assume that it does, which is very likely.

Install your new disc. Boot into the live cd and start gparted. Set up a partition on it. Still in the live cd, copy your /home into the new partition. Make sure that you can access it, and that the files all look ok.

Run the installer. Let it overwrite the existing installation, and mount the new partition, without formatting, as /home. You do both of these things by choosing the manual option when the installer gets to the partitioning stage.

Here is some reading:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)
[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

edit:
and I just found this one:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

---

### Post by b1lancer on 2009-12-15
Thanks a lot! Very informative. Excellent.


Is there any way that once I format a partition using Linux that I can view it within Windows?

---

### Post by coffeecat on 2009-12-15
> **b1lancer said:**
> Is there any way that once I format a partition using Linux that I can view it within Windows?

There are a couple of 3rd party ext2/3 drivers for Windows. One won't work with the 256-byte sized inodes that have been the default in ext3 for the last year or two. The other is said to be compatible with the larger inodes but I don't know whether it will work with the newer ext4 filesystem.

If you want a data partition to be shared between Ubuntu and Windows, the simple choice is the Microsoft filesystem NTFS. Ubuntu reads and writes to NTFS reliably and you'll have Windows available if and when you need to repair any filesystem corruption.

But whatever you choose, as a previous poster has said, backup anything of value.

And then back it up again. :wink:

---

