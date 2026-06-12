---
title: "Correct side-by-side installations"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by Arkamond on 2011-06-08
Hello, I am very new to HDD and installing operating systems and such. Although I am very skilled in other computer fields.

So I was wondering, I have a new 232 gig external HDD and I want to install Ubuntu and Win 7 ultimate onto it. (Mainly for on-site fixing of computers) 
What all is needed? I downloaded the latest ISO of Ubuntu and burned it to a DVD with Infrarecorder and booted it up. But it only displays my internal HDD and has no options to partition and install onto my external HDD. I can set the boot-loader to my external but im not sure how all of this works.

So how do I partition with the installer disk onto my external and what partitions do I need to make? (I run Win 7 home edition x64 on my internal HDD)

And then once thats installed how do I create partition for Win 7? (Ultimate x64 and x86) 

Im really new to this stuff and nothing on the other forum posts makes sense to me at this moment. 

Thanks!

---

### Post by oldfred on 2011-06-08
Is the external a USB drive. I am not sure windows installs to external drives. It wants to see the same hardware on every boot. Ubuntu is flexible except for video drivers which may be a problem.

I do not have external hard drive but installed the windows repair ISO to a flash drive, and created a flash drive with many ISO so I can boot & repair one or the other versions. I also have a full install of Ubuntu on a flash drive. So I use a lot of flash drives, not one hard drive.

If windows does work it has to be installed to a NTFS primary partition with the boot flag. Ubuntu can be installed to logical partitions and work just fine.

Why is gparted not showing sdb as a drive. Does BIOS see drive?

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

If you want multiple ISOs on one flash drive:
This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
MultiSystem Another LiveUSB Multiboot
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

---

