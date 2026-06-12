---
title: "Dual Boot Problem Grub Rescue"
date: 2010-06-06
forum: Installation &amp; Upgrades
---

### Post by bbking67 on 2010-06-06
I am having difficulty making Ubuntu dual-boot correctly with XP, and I think I have covered most of the basics.

I tried two methods to install with identical results on my brand new 320GB.  The first time I installed XP in a partition (100GB) and configured it.  Then using Ubuntu 10.04 I installed using the option to use the available free space.

After the install I got the dreaded "error: no such partition", and then a prompt saying "grub rescue>".  I followed some tutorials from here to try and revive the partition using the live CD and various grub commands to re-install, etc.  It did not work.

At that point I decided that I would try and re-install XP to the entire drive and then let Ubuntu resize the partition and install itself.  Seemed like a good idea at the time.  So after the text portion of the Windows XP install the system rebooted to a different boot error (disk error press ctrl + alt+del to restart).  This is where things got weird.  I tried FDISK/MBR with DOS and the FIXBOOT/FIXMBR commands in Windows Recovery Mode with no success.  Re-installing Linux resulted in bringing back the "grub rescue" prompt again (even though I tried re-installing to the entire drive).  I also used WD Diags to 000 all sectors on the disk (did not help but it took hours).  The fix for me was to use Acronis Disk Director to delete all partitions and create a single FAT32 as active and primary partition.

After that I was able to re-install Linux with no problems booting afterward.

Could it be that the system (an old HP nc8000 laptop) has a buggy BIOS as far as the LBA translation for the drive?  I updated the BIOS somewhere in there, but it also did not help.  Is there a way to try and figure out what can be done without having to spend 3-4 hours re-installing everything from scratch?

Any help or direction would be great at this point...

/bbking67

---

### Post by wojox on 2010-06-06
Are you installing boot.ini and grub2 to the MBR each time? I use this here [Reinstalling from LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by bbking67 on 2010-06-06
I have no idea.  I just followed the process I described.

---

### Post by darkod on 2010-06-06
If you stopped after the first install, there were things to investigate. I never recommend to make another reinstall right away, unless it is clear that a major mistake was done during the first install.

You did the right thing, when planning to dual boot you should install windows only on a part of the disk, leave the rest as unallocated and then install ubuntu there.

The no such partition error might have been this for example [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:search). But now we can't know for sure.

So what is the end result now, you have only ubuntu? And what do you want to do? Install XP again?

If ubuntu is taking the whole disk now, I don't see any other option than installing XP again on 100GB partition, and then ubuntu. If again grub2 error is present, we'll investigate.

---

### Post by bbking67 on 2010-06-06
Well, I may want to install XP again.  Now that I have Linux on there is it possible to resize Linux and add an XP partition?

I also noticed that there is a "--force-lba" switch... I'm wondering if that couldn't have helped me?

/bbking67

---

### Post by darkod on 2010-06-06
> **bbking67 said:**
> Well, I may want to install XP again.  Now that I have Linux on there is it possible to resize Linux and add an XP partition?

I also noticed that there is a "--force-lba" switch... I'm wondering if that couldn't have helped me?

/bbking67

It might be possible but I'm not sure it's worth it for a new linux install that still has no data in it. Shrinking could possibly corrupt things, or make grub2 search for core.img at the wrong place if core.img gets moved during the shrink.

It's up to you. If you want to try, use Gparted from live mode.

---

### Post by bbking67 on 2010-06-07
okay i am going to wipe the drive and re-install.  can you recommend a sequence i should follow?  My basic plan would be to:

1. Install XP in a 160GB NTFS partition
2. Install linux using the remainder of the space

How do I install grub?  I was under the impression that this would happen automatically?  Or should I create a small partition for grub?  Back in the day I used to use system command and the OS/2 boot manager with a small partition... are there advantages to doing that?

Suggestions?

---

### Post by darkod on 2010-06-07
> **bbking67 said:**
> okay i am going to wipe the drive and re-install.  can you recommend a sequence i should follow?  My basic plan would be to:

1. Install XP in a 160GB NTFS partition
2. Install linux using the remainder of the space

How do I install grub?  I was under the impression that this would happen automatically?  Or should I create a small partition for grub?  Back in the day I used to use system command and the OS/2 boot manager with a small partition... are there advantages to doing that?

Suggestions?

The plan is good. Install XP into 160GB ntfs partition, leave the rest of the space as unallocated (that's very important, no partition).
In the ubuntu installer just use the Use Largest Available Free space option.
Or Manual Partitioning if you prefer (that would allow you to create separate /home partition if you want).
As for grub2, you don't need to do anything if you have one hdd. For multiple hdds it's always best to check where grub2 will be installed, to avoid surprises. :)
You can do that: in the step 4 when asking how and where to install, note the name of the disk (/dev/sda, /dev/sdb, etc). In the last screen of the installer, before clicking Install, click on Advanced and it will show you where it plans to install grub2. Make sure it's the same disk.

That's it.

---

### Post by bbking67 on 2010-06-07
Okay thanks.  I expect to get the grub rescue console again since this is the process I used the first time, but I'll put more effort into resolving the issue (I previously just thought I did something stupid).

/bbking67

---

### Post by efflandt on 2010-06-08
There might still be a BIOS issue booting farther out on the drive, that you would not notice booting a partition at the bottom of the drive.  I have one PC that does not like the new 10.04 partition alignment (on 1 MB boundaries instead of cylinder boundaries).  Fortunately I tried 10.04 from a USB drive first, so I sorted out that I needed partman/alignment=cylinder kernel boot parameter (including booting install CD or iso on USB flash).

But there is one other issue I have not resolved yet.  That PC now boots fine from a 160 GB USB drive, or the far 32 GB end of its 200 GB internal drive.  But it will not boot a partition farther out on a 500 GB USB drive (grub rescue error: unknown filesystem).  In fact grub rescue shows unknown filesystem even for the first ntfs partition.  grub (1.98) on my main hard drive can read directories on the ntfs partition, but still shows unknown filesystem for the ext3 Linux partition.  Linux itself has no trouble auto mounting and reading any partitions on the drive.  The 500 GB USB drive boots fine on 2 other computers.

I don't know the exact point that breaks it, but it seems to be somewhere between 200 GB and 500 GB.

Just a possibility to be aware of.  If that happens again after installing both OS's, you could always make a small /boot partition, then Windows, then the rest of Linux, because once the kernel loads from /boot it should be able to access the whole drive.

---

### Post by bbking67 on 2010-06-08
I think this is my situation.  It's an older laptop and I think the BIOS LBA translation is a bit wonky.
 
How do I create a small boot paritition for GRUB?  What sequence would I follow to do it that way?  I'm a bit lost here because I don't really understand grub or Linux very well (but I used to do this in my OS/2 days).
 
Some guidance would be very helpful because I have already invested way too many hours into this! :p

---

### Post by darkod on 2010-06-08
OK, if you are willing to reinstall (again), it's the easiest way.

First boot with ubuntu cd, open Gparted and create primary ext4 partition of 200MB. That way it will stay at front.

Then you might as well create another primary ntfs 160GB partition for XP.

Boot with XP cd, install in the ntfs partition.

Boot with ubuntu cd, in step 4 select Manual Partitioning. Click the 200MB partition (should be /dev/sda1 probably), click the Change button, select ext4 for filesystem, select format, mount point /boot.

After that create / and swap in the unallocated space after the XP ntfs partition at will. You might also want to create separate /home partition at this point, it makes future cleans installs easier.

Do you need more detailed instructions for this part? In general, you just create the partition, select the size you want, filesystem and mount point.

---

### Post by oldfred on 2010-06-08
If you want to reinstall Darko's instructions are find. But you only need 200 to 400MB of space and can just create a new partition. I did that once after the install by moving all the /boot files and reinstalling grub & editing fstab, but decided I really wanted a /grub partition so I moved it all back and converted the /boot to /grub.

[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_boot_partition)

Per Herman you should only use the /boot if you have the BIOS limits issue (in old grub it was error 18).

Note that many of the repair chroot commands do not include a separate /boot and if you ever have to repair it be sure to also mount the /boot partition.

---

### Post by houseworkshy on 2010-06-08
Slightly off-thread but not too far I hope.  For windows, especially unsupported windows, it can be a lot easier just to bung it in virtual box.  In the free cripple-ware version one is unable to use the removeable drives (cd/dvd and flashsticks ) however this isn't such a huge problem as one can tell it that an iso is it's CD/DVD and go from there.

---

### Post by bbking67 on 2010-06-09
> **houseworkshy said:**
> Slightly off-thread but not too far I hope. For windows, especially unsupported windows, it can be a lot easier just to bung it in virtual box. In the free cripple-ware version one is unable to use the removeable drives (cd/dvd and flashsticks ) however this isn't such a huge problem as one can tell it that an iso is it's CD/DVD and go from there.
 
Not off-topic for me.  That's what I did last week... I installed Virtualbox with XP.  The problem is that it's just too darn slow!  My system is an older P4 laptop with only 512MB of RAM and it is inadequately equipped to run XP.  I might be able to get away with a Windows ME or 98 installation (and that might meet most of my needs), but without upgrading the hardware it's a non-starter.  The machine runs XP like a champ if it's in its own partition... but the hits for virtualization is just way to high.
 
/bbking67

---

### Post by bbking67 on 2010-06-12
Okay I have tried darkod`s suggestion and it failed to work.  basically after the XP reboot the system hangs on a blinking cursor.  very strange.

I am re-installing using a much smaller XP partition and I have switched that partition to FAT32.  The theory here is that if the LBA limit is lower than the theorized 200GB it might do the trick.  The laptop originally shipped with a small 60GB drive, so I thought it might be best to stick to that size.  Also, NTFS was a source of problems previously when my partition table was fouled up... the `fix`was to create a FAT32 partition using Acronis (after unsuccessfully trying FDISK /MBR, FIXBOOT and FIXMBR and a bunch of stuff in gparted).

so we shall see soon...

Okay I got it working!  Thanks darkod...

So creating a much smaller XP partition (I used FAT32 as well) did the trick.  Grub installed in the wee partition and the menu comes up and bother operating systems work perfectly so far!!!  I am thrilled, and after many hours of effort, relieved!  I still have a few other kinks to work out with Lucid... so at least now I can flip back to Windows occasionally.

I wasn`t too sure how much space to allocate for the swap partition.  I left about 2GB free and used that (read something that suggested 2GB was the maximum).  I hope that works out.

/bb

---

