---
title: "Boot partitions"
date: 2010-03-05
forum: Installation &amp; Upgrades
---

### Post by FahadMKS on 2010-03-05
What is the best best partion for a 250 GB hard disk drive

---

### Post by stlsaint on 2010-03-05
To run ubuntu all you require are the /,swap partitions but more advanced installs can be done using seperate /,/boot,/home,swap. 
Some people prefer the seperate /data partition over seperate home but again this is somthing that requires more research as it is a more advanced install and if done incorrectly can greaty damage your system especially if you are dual booting. I would say study up on how partitions work then figure out how you want your system setup. Post your ideas back here for more direct guidance in the direction you want to go.

---

### Post by oldfred on 2010-03-05
Some links on partitioning. I ran my system with just root and swap and dual booted with XP for 3 years. I did add a shared NTFS partition for data that I might want in both. 

[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Partitioning basics with some info on /data
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

---

### Post by Herman on 2010-03-05
Partitioning schemes have always been a matter for personal opinions.

I think keeping it simple is the 'advanced' way of doing things. 
I just use one single partition that fills the entire disk. That way it boots quicker, I never need to resize partitions because one is getting too full, and I only need to run e2fsck on one partition. I only need to make one backup of the whole thing with one dd command to a larger hard disk. It's nice and simple and it works great. :)

The computer I'm using right now had a 64 GB SSD drive with a test Ubuntu installation in it.
It has another 1 TB hdd which is leave unplugged most of the time. The 1 TB HDD contains a dd backup of the complete operating system in the SSD, so I can fully restore it in a matter of minutes if that's ever necessary. Just having the entire  operating system in one single partition makes that an easy task. :)

---

### Post by FahadMKS on 2010-03-06
I knew the boot partiotins......... but the matter is how much is the minimum space needed to the \boot partions....

Please help me guys

---

### Post by c9-3Rr0r on 2010-03-06
My boot partition is set to 92mb, but some time ago I discover that is a bit to low make it 150-200 is good choice imo

---

### Post by FahadMKS on 2010-03-10
Will it be fine to select the option as to use the Entire disk and partition automatically rather than partioning manualy.

---

### Post by Herman on 2010-03-10
That works perfectly for 99% of computers 99% of the time.

it's the fastest and easiest and probably best way to install Ubuntu.

Since you have no data on the disk you have nothing to lose, I can't see why not.
If you have other hard disks in the same computer just make sure you select the right disk, that's the most important thing.

---

### Post by perspectoff on 2010-03-11
Depends on what you want to do. I have a single computer running Windows 7, Mac OS X, Ubuntu, Kubuntu, and Debian, all on separate partitions. If you do any of the "simple methods" as recommended by some, you will fry your computer.

Grub2 sucks (the new version of the bootloader with Ubuntu). I like to keep Grub2 quarantined within the partition of the OS it came with and not use it as my first-line bootloader.

I use Grub Legacy in the (/boot) boot partition as my first-line bootloader (used only to chainload the bootloader stored in each OS' particular partition), and it only requires 50 Mb.

If you use Grub2, a beast that grows and mutates by the week, you indeed had better be prepared for a bumpy ride and indeed should probably devote 200 Mb to the boot partition (since I have no doubt that Grub2 will grow and grow).

I use the instructions I found at Ubuntuguide:

[http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:All#Dual-Booting_Windows_and_Ubuntu)

and

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

I do run virtual machines, but I don't like to do so except on a very powerful computer with about 6 Gb RAM, as it is otherwise a slow way of doing things. Further, I hate running Windows as either a host or a guest, since it is so slow. Nevertheless, a virtual machine is a clever way just to try out a new OS.

I also didn't like Wubi, which gave me fits when I tried to install it on Windows 7 and Windows Vista. Further, using it means you will be running Ubuntu from within Windows. Blecch. that's almost as bad as running virtual machines with Windows. You are tied to Windows, and that slows things down a lot. But YMMV.

Although not necessary, I also like to put virtual machines (and pseudo-virtual machines like the Kolab server platform) in their own partitions. 

This makes it easier to run them from one of several different operating systems without having to re-install them every time. In addition, every time I upgrade a version of Ubuntu (or Windows or Mac OS-X), something fails. By having a backup partition with the old version(s), I can stay in business while I troubleshoot the upgrade(s).

So, for example, I have 2 Ubuntu Jaunty Jackalope partitions, which are identical. One of them I upgrade to Karmic Koala, which usually takes me about 2 weeks to sort out the bugs. While I am sorting out the bugs, I continue to run the system from the other partition.

There are a few users who are lucky enough to have smooth upgrades, but they are often either developers with top-of-the-line equipment or users without much customization to their systems. I use my systems for business and they are highly customized, and there is no way I want to risk losing the system during an upgrade.

Lastly, I never, ever let any one OS take up the entire hard drive. I learned that from Windows. If you let windows 7 install to the entire hard drive, you will have a devil of a time getting any of your hard drive back. Ubuntu (with Grub2, especially) is becoming similar, which I hate. But it is not as bad, yet.

You will find a lot of advice, from noobs who don't know any better, and from superusers who have forgotten the pitfalls they solved long ago. Be safe.

---

