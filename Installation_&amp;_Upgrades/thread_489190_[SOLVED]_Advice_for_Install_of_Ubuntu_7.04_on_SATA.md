---
title: "[SOLVED] Advice for Install of Ubuntu 7.04 on SATA Drive with Windows XP on Separate"
date: 2007-07-01
forum: Installation &amp; Upgrades
---

### Post by morning_napalm on 2007-07-01
I have just recently begun learning about Linux and have installed Ubuntu 7.04 on an old computer to begin learning.  I am now ready to install it on my main computer which has 2 internal drives.  One is an IDE drive with Windows XP installed.  The other drive is an SATA drive and I have just finished emptying it so that I can install Ubuntu onto it and use it as a shared drive between OS.

I have done a fair amount of searching but wanted some advice on the best way to go about this install.  I plan to just reformat and partition the SATA drive (250 GB).  I was planning to make 4 partitions:

/ partition ext3 - 20GB 
/swap partition ext3 - 2GB
/home partition ext3 - 60GB
and the remainder a FAT32 to share files (~170GB)

Do I need the /home partition?  Are these sizes about right?
Should I simply use the Recovery CD to format and partition and then use the Live CD to do the install?
Will the live CD essentially step me through the Dual Boot setup?
Is there anything special I need to do so that the system sees GRUB on the SATA drive to allow selection of which OS to launch?

I'm hoping this works well.  I could not get sound working at all on my old system and could not get 3D rendering to work on the ATI Rage 128 card either.

Thanks for your help.  Hopefully tomorrow night I'll be up and running!!!!

---

### Post by confused57 on 2007-07-01
> **morning_napalm said:**
> I have just recently begun learning about Linux and have installed Ubuntu 7.04 on an old computer to begin learning.  I am now ready to install it on my main computer which has 2 internal drives.  One is an IDE drive with Windows XP installed.  The other drive is an SATA drive and I have just finished emptying it so that I can install Ubuntu onto it and use it as a shared drive between OS.

I have done a fair amount of searching but wanted some advice on the best way to go about this install.  I plan to just reformat and partition the SATA drive (250 GB).  I was planning to make 4 partitions:

/ partition ext3 - 20GB 
/swap partition ext3 - 2GB
/home partition ext3 - 60GB
and the remainder a FAT32 to share files (~170GB)

Do I need the /home partition?  Are these sizes about right?
Should I simply use the Recovery CD to format and partition and then use the Live CD to do the install?
Will the live CD essentially step me through the Dual Boot setup?
Is there anything special I need to do so that the system sees GRUB on the SATA drive to allow selection of which OS to launch?

I'm hoping this works well.  I could not get sound working at all on my old system and could not get 3D rendering to work on the ATI Rage 128 card either.

Thanks for your help.  Hopefully tomorrow night I'll be up and running!!!!

I would suggest you download & burn a copy of the Super Grub Disk, before you install Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
it's only a 5-7 Mb download 

You might want to look over this guide, since you have 2 hard drives:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)
for this guide to work, your bios would need to be able to boot first to your SATA drive that you're installing Ubuntu on.

I would suggest that you set up a separate /home partition...size would depend on what you'll be saving to your home directory.  Here's a couple of excellent guides for planning partitions:
[http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning](http://www.users.bigpond.net.au/hermanzone/p17.htm#help_on_partitioning)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

Some prefer to make a shared ext3 partition(instead of FAT32) and install the fs-driver in Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by morning_napalm on 2007-07-01
Thanks a bunch.  I'll try to keep a good record of what I do and post a reply once I'm successful (optmism)!  These guides all look very much like what I need.

---

### Post by morning_napalm on 2007-07-03
After much ado, I have managed to install Ubuntu 7.04 to dual boot with Windows XP on my desktop.  Some of the specifics are:

Intel Motherboard
Intel Pentium 4 2.8GHz processor
SB Audigy Sound Card
Samsung 250GB SATA Drive (Ubuntu Installed Here)
WD 120 GB IDE Drive (Windows XP installed here)
NVidia GeForce FX5600 Video Card

Here is what I did.

**Step 1:**

Used GParted Live CD to set up my 250 GB SATA drive for installation.  It did not want to autoconfigure xorg, but I selected the nv driver and 1024x768 rsolution and it worked fine.

After a lot of fumbling around and creating, resizing, etc i managed to create the following.  I definitely need to understand partitioning better and am still not sure I got exactly what I wanted.  Anyway, I set up the following partitions.

/dev/sda1 ext3 9.77GB
/dev/sda2 ext3 221.16GB
/dev/sda3 linux-swap 1.95GB

**Step 2:**

I then rebooted into Windows and installed fs-driver so that Windows could read/write to the new /home or shared file partition.

**Step 3:**

I rebooted again with the Ubuntu 7.04 Live CD and began the install.  I manually partitioned the drives and simply selected the partitions I had already created and assigned them to / root, /home, and swap was already identified.  At the end, I let it install grub to (hd0) which I think is where the Windows MBR is located.  I read several posts suggesting not to mess with the MBR, but decided to trust Ubuntu and go for it.  I admit I was a bit afraid what would happen when I rebooted.....

The system kind of locked up when I tried to restart and remove the CD.  I ended up just powering down and then quickly ejecting the CD when I started back up.  GRUB loaded and I had all of the options I need to Boot to Ubuntu or Windows XP.  I tried XP first and it worked fine.  I copied some files to the shared partition and then rebooted into Ubuntu.

**Step 4:**

After booting into Ubuntu, there were 72 updates to install.  I did this first.  I rebooted when it asked and all is good!

I installed the Nvidia-glx driver (suggested when I went to desktop effects).  I had to restart again to use new video driver. I do need to figure out how to set my screen resolution to 1280x1024 which is the native resolution for my monitor.  I've done some searching, but have more looking to do.

Thanks for the help.:D  Hopefully this will help some others trying to do something similar.

---

