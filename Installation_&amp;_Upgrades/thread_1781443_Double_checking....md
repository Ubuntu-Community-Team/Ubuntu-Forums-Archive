---
title: "Double checking..."
date: 2011-06-13
forum: Installation &amp; Upgrades
---

### Post by ojdon on 2011-06-13
Hi there, I'm wanting Ubuntu 11.04 (64-bit) on my current system which currently has Windows 7 Home Premium (64-bit) installed just want to double check this is the correct method to go about installing Windows 7 and Ubuntu 11.04 side by side so:

1. Resize Windows 7 partition to give me 15GB free space (What's the best way of doing this GParted or Windows' own partition editor)

2. Insert the Ubuntu 11.04 Live USB hit installed, when it asks me what I want to do with the hard disk I click on "Something else"

3. From here I make a 256mb /boot partition (Ext2 the best format for this?)

Use the remaining disk space to create a "/" partition formatted in BTRFS. (Do I need to make a swap partition considering I have 4GB of ram, if so how much swap?) 

Hit install, sit back and relax!?! Would this install Grub/etc? I'm considering making a custom kernel using KernelCheck if everything goes smoothly with this installation nothing is stopping me right?

Also just in case this might help here is my laptop spec:
Intel Core 2 Duo (2.2GHz)
4GB DDR3 RAM
Nvidia GeForce 240M
320GB SATA Hard Drive

Thanks!

---

### Post by Quackers on 2011-06-13
First make sure that Windows 7 is not using all 4 available primary partitions. If it is, don't create another until you have deleted one of them!
Secondly, if you are going to shrink a Windows partition you should defragment it first - twice would be better.
Then you should use Windows Disk Management console to shrink it.
Then you can boot from the Ubuntu live cd/usb and select "try Ubuntu" to make sure your hardware works with 11.04.
Then you can install Ubuntu to your hard drive from the live desktop.
There is normally no need for a separate boot partition.
You can use the "install alongside" option if you want a standard installation. However, if you want to manually partition (or to have a separate /home partition) you can choose the "something else" option.
1GB of swap would be more than sufficient unless you are intending to use hibernation, in which case you would need about 4.5GB swap. But no swap at all is possibly ok too.
The default file system for Ubuntu is now EXT4. I'm not sure if BTRFS is fully supported at this time.
Grub would default to /dev/sda, which is the first hard drive read by bios, unless specifically instructed to install somewhere else. Not usually a good idea.

Looking at your graphics card it may be necessary to use the "nomodeset" boot option for both the live cd and the first boot of the installed system. Otherwise you may not get video. Try it without first.

---

### Post by Frogs Hair on 2011-06-13
I dual boot an find it easier for me to use Windows disk management . I don't hibernate , so I use very little swap. When I started with a Wubi installation it only set a side 256 Mb of Swap and that is all I use now.

---

