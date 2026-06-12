---
title: "Boot from SSD alongside RAID 0 ?"
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by thenewasbo on 2012-09-14
Would it be simpler to try to install Ubuntu on a separate SSD if I already have 2 HDDs running in RAID 0? I had a lot of trouble trying to get GRUB to work properly on my RAID 0 HDDs and I would rather not mess with it again.

Running Windows 7 64-bit off of 2 HDDs in RAID 0.

---

### Post by oldfred on 2012-09-15
With RAID you need to use the alternative installer, which is not a liveCD.

If just installing to a SSD, then you could do a normal install and then add the RAID drivers and reconfigure, but I do not know RAID nor exactly how to do that.

You do know RAID 0 is not really recommended.
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes file system creation and modification support, except for file system probing to determine what's in a partition.

For RAID reinstall from liveCD
sudo apt-get install mdadm

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ubuntuforums.org/showthread.php?t=1777458](http://ubuntuforums.org/showthread.php?t=1777458)

---

### Post by thenewasbo on 2012-09-15
Thanks for the reply.

Even if I wasn't using RAID, I was more curious about installing Ubuntu to a separate SSD. Is it possible to do that without messing without installing GRUB, which is what I believe is used to boot into Ubuntu. Is it possible to use what Windows 7 uses to choose which OS to boot to instead of installing GRUB?

---

### Post by oldfred on 2012-09-15
You have to have grub as it boots Ubuntu.

Windows boot loader only looks for a partition with the boot flag and jumps to code in the PBR or partition boot sector. Grub is not normally installed to a PBR. 

Some with Windows use another third party modification of Windows.
[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

No idea if it even works with RAID or SSDs.

 I like grub2 and most here use grub2. It has extra modules that it loads to see LVM, RAID and other special cases.

When you have multiple drives, I prefer to have a different boot loader in each drive and each install in the same drive. Then when one drive fails I can still boot the other. I have different Ubuntus's in 3 drives and XP in a 4th, but do not use XP now with my SSD as I had to change to AHCI with the SSD and do not have the AHCI driver installed in XP. 

Lots of details on SSDs:
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by thenewasbo on 2012-09-15
So if I put in an extra SSD, could I install GRUB straight to the SSD without touching the RAID drives? I want to have an SSD just dedicated to Ubuntu and I don't need access to my other drives when using Ubuntu.

---

### Post by darkod on 2012-09-15
Don't let your experience with grub2 and your raid put you off using it. As already mentioned, you probably had problems because you used the standard live cd to install onto fakeraid, not the alternate which is recommended.

The grub2 bootloader is much superior to the windows one in any way.

You can install ubuntu to a separate disk outside your array if you want to, no problem. Simply install grub2 to the same disk and it won't touch anything on your raid. Case closed.

I suggest you use the manual partitioning when installing (option Something Else) because that gives you best control what goes where including the bootloader.

---

### Post by thenewasbo on 2012-09-15
I see. Well, I used the alternate disc, because it said it was for RAID. I'll use it again once I get an SSD. I'm not entirely sure about the settings for the manual partitioning though. I looked at it and didn't really understand all of the options.

---

### Post by darkod on 2012-09-15
The manual partitioning is not that complicated. Where did you get stuck?

On a new disk, it would show only the disk like /dev/sdc for example. Select it and it will ask you if you want to write a new partition table (because new disks don't have any usually). Confirm, and after that it will show FREE SPACE under /dev/sdc.
Select the free space and it will ask you to create a partition. Choose size, primary/logical, beginning or end in the free space.
Once created, select that partition and select use as ext4, and mount point /.
That's it.
Create other partitions you might want like that, like /home.
When creating the swap, the use as is swap area and it doesn't have mount point.

If you used the alternate cd it should have installed grub2 correctly. Sometimes it can't get the array right, so if it asks you for a grub2 destination you need to give it the array name, but only the array, without any partition numbers. For example it would be something like:
/dev/mapper/blah_blah

and it should not end in numbers, or p1, p2, etc. There are rare exceptions from this too.

If you want grub2 on /dev/sdc, select that as destination and that's it.

For installing on separate ssd you can use the live cd, you don't necessarily need the alternate cd. The manual partitioning is little different and graphical, but the same applies.

---

