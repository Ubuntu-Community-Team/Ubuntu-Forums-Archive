---
title: "Boot Repair with weird configuration"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by areeda on 2011-08-07
I did get this to work, so I'm posting to perhaps help others and see if there is an easier way.

It's a new system:

ASUS P8Z68-V Pro motherboard
I7-2600K 3.4GHz
16GB 1600MHz RAM
NVidia GTX560
Corsair 260GB SSD
3x Barracuda 2TB 7200RPM drives

Running Ubuntu 11.04 AMD64 and Win 7 Pro 64

So I installed Ubuntu first, then Windows.  I knew the MBR would be hosed but recovery was more trouble than I expected.

Because of the SSD, I set up the disks to have system files on the SSD and more rarely used files on the hard drives.  It's still not perfect but that's a topic for another thread.  The point here is that I have 3 Linux partitions,  / on the SSD, /usr in one HDD and /home in another.

Because of 2 SATA controllers and some moving things around the SSD is /dev/sdd and the /usr is on /dev/sdc2.

The first issue when you run Boot Repair (see [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) you need to run apt-get but the /usr (specifically /usr/bin) is not mounted only /.

So before running the chroot command we have to mount usr.

Then the default drive to install grub I think was /dev/sdc.  I have no clue why.  The only way (I found) to get the boot loader on the proper drive was to run Boot Repair twice.  On the second try we get the choice of which drive to install it.

If you have a better way, I'd like to learn it.

Joe

---

### Post by allwimb on 2011-08-07
Thank you joe for this mini tutorial it's very interesting.

[spring login]("http://www.java-forums.org/blogs/spring-framework/531-login-forms-spring-security.html")

---

### Post by conradin on 2011-08-07
install windows first. Then Linux. Thats the easiest way

---

### Post by areeda on 2011-08-07
> **conradin said:**
> install windows first. Then Linux. Thats the easiest way
That's true but if you're using the Windows System Builders license you really only get one shot at where it's installed and even with the retail license you can only have one copy on the system at a time.

When I build a system I almost always install Linux first to do the burn in testing, even if it will be Windows only.

I suppose installing another variation after Windows would fix it also.  That would probably have been quicker than figuring this out.  Even if I just deleted it afterwards.

I guess I find Windows installation to be a lot less flexible so I tend to do my experimentation with Linux and add Windows when I'm done.  Perhaps I should get in the habit of doing a clean Linux install after Windows.

Joe

---

### Post by oldfred on 2011-08-07
Some with very small SSD may need to do what you did, but I tend to want to have an entire operating system on one drive with the boot loader on the same drive. With your SSD you want both Windows & Ubuntu on the SSD and that is ok, but keep all the system files on the SSD. Then put data on the hard drives. I believe hard drives fail and if system is on multiple drives any drive failure takes system down. I go for reliability over speed or other reasons for splitting system.


Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)

Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by areeda on 2011-08-07
Fred,
I understand most of the issues with partitioning.  What I'm struggling with is SSD limited writes and what it speeds up and what it doesn't.

I'll probably do a reinstall soon as I get done fighting with Windows.

I think /usr/lib will benefit from the SSD speed which is significantly faster than the HDD:

The Ubuntu disk benchmarks look like this.  The read/write rates are in MB/s and access times are in ms.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=199523&stc=1&d=1312772032[/IMG]

I think it's reasonable to limit the SSD's use to those things that benefit.  I may be wrong but I'm still learning.  It was the most expensive piece in this system.

Joe

---

### Post by oldfred on 2011-08-07
An SSD is on my short list of next things to buy, so I am saving links.

[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)
[https://wiki.ubuntu.com/MagicFab/SSDchecklist](https://wiki.ubuntu.com/MagicFab/SSDchecklist)

Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)
Tuning Solid State Drives in Linuxcheckbox
[http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/](http://cptl.org/wp/index.php/2010/03/30/tuning-solid-state-drives-in-linux/)

BIOS settings (SSD but also most systems)
[http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561](http://www.ocztechnologyforum.com/forum/showthread.php?79848-THE-BASIC-GUIDE-amp-FAQ-ABC-for-OCZ-SSD&p=567561&viewfull=1#post567561)

Your new system probably has UEFI with a BIOS mode. Windows will boot from UEFI on gpt partitioning, but if anything grub2 does not seem to dual boot well with UEFI. One suggestion is to install Ubuntu first if using UEFI and windows second or totally back up windows efi boot partition and restore after Ubuntu is installed.

---

### Post by areeda on 2011-08-08
I have to say that I don't see an amazing speed difference.  I'd like to try a 10,000RPM drive like the Velociraptor.  The SSD does make a big difference and I'm probably still in a sub-optimal configuration.  Bottom line is I'm still not convinced that it's worth the money.

The drive I selected the Corsair 240GB Force Series is about $2.13/GB vs The 2TB Barracuda at $0.04/GB vs the Velociraptor at $0.41/GB.

There is certainly more to it than $/GB, since this is about performance and reliability more than bulk storage but I'm not in a cost doesn't matter situation by any means.

I have a lot to learn but overall I'm pleased with the purchase.

Joe

---

### Post by oldfred on 2011-08-08
I am only considering a smaller SSD as a boot only for Ubuntu. I use 25GB for a / (root) so with 60GB the current popular size I can have two versions in my SSD.

I recognize that SSDs only speed up certain things. I cannot type faster, nor download from Internet faster. I do not compile large programs, so it is mostly for booting faster and loading large programs faster. But Firefox loads pretty fast as it is.

---

### Post by YannBuntu on 2011-08-10
Hello, I am the dev of Boot-Repair. Thanks for your bug report. Please next time, use this bug tracker: [https://bugs.launchpad.net/boot-repair/](https://bugs.launchpad.net/boot-repair/) , so that I can be warned quickly. (hopefully I saw this thread!)

As you saw, separate /usr partition is not managed by the current [stable Boot-repair version]("https://launchpad.net/~yannubuntu/+archive/boot-repair"). But in the [development version]("https://launchpad.net/~yannubuntu/+archive/boot-repair-dev") I managed to make it compatible with separate /boot , so I may also consider doing the same for separate /usr if you are not the only one to ask this feature ;)

> **areeda said:**
> the default drive to install grub I think was /dev/sdc.  I have no clue why.

In next version, you will have the choice whatever the situation :)

---

### Post by areeda on 2011-08-10
> **YannBuntu said:**
> Hello, I am the dev of Boot-Repair. Thanks for your bug report. Please next time, use this bug tracker: [https://bugs.launchpad.net/boot-repair/](https://bugs.launchpad.net/boot-repair/) , so that I can be warned quickly. (hopefully I saw this thread!)

As you saw, separate /usr partition is not managed by the current [stable Boot-repair version]("https://launchpad.net/%7Eyannubuntu/+archive/boot-repair"). But in the [development version]("https://launchpad.net/%7Eyannubuntu/+archive/boot-repair-dev") I managed to make it compatible with separate /boot , so I may also consider doing the same for separate /usr if you are not the only one to ask this feature ;)



In next version, you will have the choice whatever the situation :)
Thank you.

To be honest, I didn't consider the fact that boot-repair didn't handle my situation a bug.  I was thinking it was more that I was doing something out of the ordinary.  I am happy to file things like this in launchpad as an RFE.

We all appreciate your efforts to fix our missteps.

Joe

---

### Post by YannBuntu on 2011-08-11
ok, thanks for your reply.
By the way, the new version has landed in the stable PPA :) 
--> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

