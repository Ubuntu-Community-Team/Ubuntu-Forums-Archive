---
title: "Install Question"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by Willie G on 2007-02-17
I want to install Ubuntu on my laptop computer.  The laptop came
with Windows Vista preloaded and some recovery disks that are of
questionable value.  There is one big partition on the drive (C) and
one 9gb. recovery partition (D).  I don't want to try to mess with my
partitions, so is there anyway to install Ubuntu without disturbing
or having to modify the existing 2 partitions on my hard drive?

---

### Post by mikewhatever on 2007-02-17
No, don't think so. Space must be freed to create Ubuntu partitions, so the only solution is to resize one of the existing ones, presumably not the recovery. I have a similar setup, apart from another partition for Quick Play system. If you have to have Ubuntu, but do not want to modify the exsting partitions, consider installing on a removable USB drive.

---

### Post by solar george on 2007-02-17
Resizing the windows partition shouldn't be too much of a problem.
[https://help.ubuntu.com/community/forum/installation/Partitioning]("https://help.ubuntu.com/community/forum/installation/Partitioning")

The other options would be to buy an extra harddrive and swap them over to change between windows and linux (not a good idea), and to install linux on a usb disk - providing your laptop can boot from one.

---

### Post by Willie G on 2007-02-17
Thanks for the replies. I'm looking now at the link in the previous post. 
I don't have anything installed on this computer yet, and I realize that 
there is a chance that the Windows installation could be damaged.   

I am unable to create any type of partition through Windows because I
was dumb enough to buy a preloaded computer without an actual OS disk.
I can restore the computer to the factory Vista installation,  but I cannot 
partition the drive through Windows.

I just want a method that isn't very likely to totally blow away my Windows
Vista installation or the recovery partition.

---

### Post by benson444 on 2007-02-17
Unless you can reinstall Vista from scratch, or are prepared to lose Vista completely then do not try to install another OS. It's a pretty major choice. You should back up everything you don't want to lose and be ready for the worst.

It may go fine, but if it doesn't you will be very unhappy and end up blaming Linux.

---

### Post by Willie G on 2007-02-17
> **benson444 said:**
> Unless you can reinstall Vista from scratch, or are prepared to lose Vista completely then do not try to install another OS. It's a pretty major choice. You should back up everything you don't want to lose and be ready for the worst.

It may go fine, but if it doesn't you will be very unhappy and end up blaming Linux.

I don't blame Linux  I blame a vendor who sold me a laptop computer
promising me over the phone that I would get a Windows OS disk and
have access to Windows RE tools,  then lying to me and sending me a 
crappy recovery disk, leaving me unable to perform any hard drive
partitioning.

---

### Post by Willie G on 2007-02-17
More weirdness

In Windows Vista using the disk management tool I 
see a new partition "E" with a volume "Ubuntu 6.061.i
698 MB CDFS" (?) when I have Dapper Live CD in 
the drive even if I boot from hard drive ( vista ).

Heck with it
I'm just going to let Ubuntu install.  I'm not totally crazy 
about Vista anyway.

---

### Post by eapache on 2007-02-17
It's showing the cd as a partitioned drive. when the cd is removed, and the disk manager is refreshed, there should be a blank line that says something like "E: no disk inserted"

---

### Post by Willie G on 2007-02-17
> **eapache said:**
> It's showing the cd as a partitioned drive. when the cd is removed, and the disk manager is refreshed, there should be a blank line that says something like "E: no disk inserted"



I should have seen that,  But I have been up for 48 hours and I'm a little punchy.

---

### Post by Skidpad on 2007-02-17
> **Willie G said:**
> Thanks for the replies. I'm looking now at the link in the previous post. 
I don't have anything installed on this computer yet, and I realize that 
there is a chance that the Windows installation could be damaged.   

I am unable to create any type of partition through Windows because I
was dumb enough to buy a preloaded computer without an actual OS disk.
I can restore the computer to the factory Vista installation,  but I cannot 
partition the drive through Windows.

I just want a method that isn't very likely to totally blow away my Windows
Vista installation or the recovery partition.
1) There aren't many computers sold these days that have actual OS disks included.  The recovery disks will do the same thing as an OS disk for the most part (except MS utilities).  Unfortunately they contain all of the extra garbage from the OEM's that isn't part of a normal Windows installation.

2) You won't need to partition through Windows to install Ubuntu - the Ubuntu installation disk contains "GParted" that will allow you to see your existing partitions and file structure, and then setup new partitions manually/automatically.

---

### Post by Willie G on 2007-02-18
> **Skidpad said:**
> 1) There aren't many computers sold these days that have actual OS disks included.  The recovery disks will do the same thing as an OS disk for the most part (except MS utilities).  Unfortunately they contain all of the extra garbage from the OEM's that isn't part of a normal Windows installation.

2) You won't need to partition through Windows to install Ubuntu - the Ubuntu installation disk contains "GParted" that will allow you to see your existing partitions and file structure, and then setup new partitions manually/automatically.


I just ended up using Gparted and everything is going well so far.

Now I can have fun configuring my wireless adapter.

Thanks to everyone for their help.

---

