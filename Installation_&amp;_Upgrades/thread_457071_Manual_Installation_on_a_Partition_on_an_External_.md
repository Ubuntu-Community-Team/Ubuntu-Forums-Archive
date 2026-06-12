---
title: "Manual Installation on a Partition on an External HD"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by naruto137 on 2007-05-28
I don't know how to install Ubuntu 7.04 onto the installation HD. This is my backup HD for Vista but I also want to install Ubuntu on this. I partitioned 20GB on the drive so it now has 2 partitions. I want to install Ubuntu on the 20GB partition. The installer asks me in the "Prepare disk space" part of the installation guide "How do you want to partition the disk? If I choose Guided, use the entire disk and I select my drive, It says it will delete everything on the drive but I just want to use that partition I already made, not the whole drive. So I decide to use manual partition but I don't know how to use this. Please Help

---

### Post by confused57 on 2007-05-28
This desktop install guide has some excellent screenshots:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

For manual partitioning, make a new partition of approx 19 Gb for the root  partition(you might want to select it as a  logical partition), format ext3, set the mountpoint as (/)...use the rest for swap(logical partition), mountpoint swap, format as swap.

One important thing to keep in mind is NOT to install grub to your internal hard drive mbr...if you do, you won't be able to boot Vista with your external hard drive disconnected.  If you can boot first to a USB device(your external drive), you shouldn't have any problems.  What you would probably do is set the external drive to boot before your internal drive in bios, before you boot up the desktop live cd to install Ubuntu.  Be sure to watch for where grub is going to be installed, the default is (hd0)...you might want to change this to "/dev/sda", substitute sda for however your external is identified.  This should ensure that grub is installed to the mbr of the external hard drive.

If your bios is not capable of booting first to a USB device, leave your boot order internal first...but be sure to install grub to the external hard drive mbr...this is very important, for the reason I mentioned earlier.
Set up this way, you would need the Super Grub Disk to boot your external hard drive:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
or you might be able to boot Ubuntu from Vista, using EasyBCD:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
this would require installing grub to the root partition, e.g.  /dev/sda3, or whichever is the root partition

You can set it up however you want, I just wanted to mention the possible problems with installing grub to your internal hd mbr.

---

