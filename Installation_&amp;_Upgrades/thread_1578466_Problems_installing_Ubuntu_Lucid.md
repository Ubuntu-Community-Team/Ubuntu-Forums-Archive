---
title: "Problems installing Ubuntu Lucid"
date: 2010-09-20
forum: Installation &amp; Upgrades
---

### Post by KKoudelka on 2010-09-20
I have Ubuntu installed on my labtop and I love it!  So I'm trying to install it on an older desktop that I have and everything seems okay until......
Installation is complete you need to restart the computer.... 

 I hit okay and I get: (with different memory segments)

[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776

,,,

[33354.539493] end_request: I/O error, dev sr0, sector 526776

Which fills up the whole screen and the cd ejects automantically. 
I have to restart to exit this

After restarting I get:

error: couldn't read file.
error: you need to load the kernel first.

    failed to boot both the default and fallback entries.
press any key to continue...

then goes to grub bootloader screen

after selecting ubuntu generic

error couldn't read file
error you need to load the kernel first

Anyone know how I can fix this. 

I've tried installing along side WindowsXP and then I tried installing on the whole hard drive.

---

### Post by perspectoff on 2010-09-20
It didn't install correctly. Just try again.

The installer needs a certain amount of RAM, so if your "older desktop" has very little RAM, try the Ubuntu Alternate version (or even the Ubuntu Server version, to which you can then add a desktop later).

---

### Post by KKoudelka on 2010-09-20
The desktop I'm trying to install to has 2 gigs of ram.  I've tried installing 4 times and I've reburned the disk and keep getting the same results

Installation is complete you need to restart the computer.... 

 I hit okay and I get: (with different memory segments)

[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776
[33354.539493] end_request: I/O error, dev sr0, sector 526776


I keep re-burning it to the same CD-RW (I'm low on cd's). I'll try to re-burn the
Server version and see if it works.

---

### Post by Iowan on 2010-09-20
I've had a couple of instances where a CDRW didn't work, but the same image burnt to a CD worked fine.

---

### Post by perspectoff on 2010-09-20
> **Iowan said:**
> I've had a couple of instances where a CDRW didn't work, but the same image burnt to a CD worked fine.

Agreed.

---

### Post by KKoudelka on 2010-09-20
Okay I've burned the alternate version to a CD-R.  After restart I get 

error: could'nt read file
error: you need to load the kernel first

       Failied to boot both default and fallback entries.

While it was installing it gave me no clues that something is wrong.  This time it took much longer to install about an hour to 45 minutes all together.

also durning the install process I wrote down this I don't know if it's any help

partition #1 of scsi1 (0.0.0) (sda) as est 4
partition #5 of scsi1 (0.0.0) (sda) as swap

creating ext 4 file system for / in partition #1 stuck at 33% for a while then the screen changed 

______________________

I installed Windows xp on this same hard drive last night and it worked fine.  I'd rather install Ubuntu though.

---

### Post by KKoudelka on 2010-09-20
okay I've restarted and get 

error: hd0,1 out of disk.

error:cannot read the linux header

error you need lt load the kernel first.

---

### Post by KKoudelka on 2010-09-20
Is there anyway to boot from the cd and install grub?

Earlier at least grub did install. Now grub doesn't even show up, but when I boot from the cd I can see all the installed files on the hard drive.  Does anyone have any ideas about how to fix this or what might be wrong?  I'd hate to have to install windows xp on it. 

I wonder it's because my computers not compatible with this install, it's a ideq biostar sff PC.

---

### Post by zealibib slaughter on 2010-09-20
you may want to make a ubuntu start up usb flash drive using the start up disk creator under system - administration from an existing ubuntu box.

---

### Post by KKoudelka on 2010-09-20
Thanks for the response a miracle happened and Ubuntu booted up!!! finally without the cd.

Before it came up grub did not load, it had this on the screen:

error: couldn't read file.
error: you need to load the kernel first.

    failed to boot both the default and fallback entries.
press any key to continue...

after pressing the key a couple of times ubuntu booted up.  Is there some way to edit grub configuration so that it boots up correctly now that am logged in to ubuntu?

---

### Post by perspectoff on 2010-09-20
> **KKoudelka said:**
> Okay I've burned the alternate version to a CD-R.  After restart I get 

error: could'nt read file
error: you need to load the kernel first

       Failied to boot both default and fallback entries.

While it was installing it gave me no clues that something is wrong.  This time it took much longer to install about an hour to 45 minutes all together.

also durning the install process I wrote down this I don't know if it's any help

partition #1 of scsi1 (0.0.0) (sda) as est 4
partition #5 of scsi1 (0.0.0) (sda) as swap

creating ext 4 file system for / in partition #1 stuck at 33% for a while then the screen changed 

______________________

I installed Windows xp on this same hard drive last night and it worked fine.  I'd rather install Ubuntu though.

Something is odd. Partition #1 (where Windows usually lives and which is usually filesystem NTFS) is now filesystem ext4 (which is the filesystem that Ubuntu uses) but the swap partition is partition #5. What do you have as partitions #2, #3, and #4? 

Is it possible you don't have enough space in the partitions into which you are installing?

The reason I'm asking is because you said you installed Ubuntu on the entire hard drive, in which case you ought to only have 2 partitions -- the root (/) partition and a linux-swap partition. Did you allow the Ubuntu Partition Manager to reformat the entire disk during installation, or not?

How big is your hard drive, anyway?

This kind of appears to me like you have a bootloader (like Grub) installed somewhere (perhaps in partition #2, 3, or 4) but it is non-functional (and unable to load its entries). However, it is not getting erased and the Master Boot Record still refers to it. That will give the errors you have now.

Can you list the partitions currently on your hard drive, their filesystem types (ext4, ext3, NTFS, FAT32, etc), their size, and numbers (/dev/sda1, /dev/sda2, etc.)? You can get this information either by:

1) running a GParted LiveCD

2) running the Ubuntu LiveCD (whichever one will boot up) and installing until you get to the partitioning section (don't worry -- you can abort before making any changes)

3) possibly by running Windows, if you still have a version that boots (which I doubt, from the sound of things).

---

### Post by zealibib slaughter on 2010-09-20
code sudo gedit /boot/grub/menu.lst or view this link [http://ubuntuforums.org/showthread.php?t=1476569](http://ubuntuforums.org/showthread.php?t=1476569). I'm not sure if lucid still uses menu.lst as the grub config file or not since all my systems was upgraded when grub 1.5 was standard so the link I gave you may be your best option.

---

### Post by perspectoff on 2010-09-20
> **zealibib slaughter said:**
> code sudo gedit /boot/grub/menu.lst or view this link [http://ubuntuforums.org/showthread.php?t=1476569](http://ubuntuforums.org/showthread.php?t=1476569). I'm not sure if lucid still uses menu.lst as the grub config file or not since all my systems was upgraded when grub 1.5 was standard so the link I gave you may be your best option.

No it doesn't. menu.lst only persists if an upgrade from Jaunty to Karmic is done.

But there is something else odd in this story. Now he says he is booting from (hd0,1), which is Partition #2. Earlier he said ext4 was in partition #1, which would be (hd0,0). He is not telling us the whole story. So it is not entirely clear to where he is installing Ubuntu (or perhaps by now he has installed it to a few different partitions, which is why it is finally booting). Grub is definitely confused, and perhaps it is just lucky that it booted.

---

### Post by KKoudelka on 2010-09-20
Yes, perspectoff I allowed the partition manager to reformat the entire disk.  The hard drive is 80 gigs.

Judging by the problems I'm having I thought it was related to the hard drive but I don't know how/where and what size for partitions to install manually so I chose to install on entire hard drive rather than choose partitions myself.

---

### Post by perspectoff on 2010-09-20
> **KKoudelka said:**
> 
also durning the install process I wrote down this I don't know if it's any help

partition #1 of scsi1 (0.0.0) (sda) as est 4
partition #5 of scsi1 (0.0.0) (sda) as swap

creating ext 4 file system for / in partition #1 stuck at 33% for a while then the screen changed 



It probably means that Partition #1 is tiny and doesn't have enough room in which to install Ubuntu.

---

### Post by perspectoff on 2010-09-20
> **KKoudelka said:**
> Yes, perspectoff I allowed the partition manager to reformat the entire disk.  The hard drive is 80 gigs.

Judging by the problems I'm having I thought it was related to the hard drive but I don't know how/where and what size for partitions to install manually so I chose to install on entire hard drive rather than choose partitions myself.

Again, then you ought to have only 2 partitions: Partition #1 and Partition #2. I don't understand how you have 5.

---

### Post by KKoudelka on 2010-09-20
> **perspectoff said:**
> No it doesn't. menu.lst only persists if an upgrade from Jaunty to Karmic is done.

But there is something else odd in this story. Now he says he is booting from (hd0,1), which is Partition #2. Earlier he said ext4 was in partition #1, which would be (hd0,0). He is not telling us the whole story. So it is not entirely clear to where he is installing Ubuntu (or perhaps by now he has installed it to a few different partitions, which is why it is finally booting). Grub is definitely confused, and he is just lucky that it booted.

I suspect his hard disk is a mess, though.

I don't think he understood the partitioning instructions during Ubuntu installation on any of his attempts.


This is now my eighth attempt at installing this and it now finally booted up.  You are right I don't now about partitioning that's why I choose to install on the entire Disk and reformat.

there are not any other partitions like ntfs

under administration/disk utility 

I see device:  /dev/sda1

type ext4

It shows volumes 77 GB ext4

Extended 3.3 GB
3.3 GB Swap

---

### Post by KKoudelka on 2010-09-20
One other thing trust me.  I'm not just creating partitions for the fun of it.  I know what a partition is and I'm not choosing to manually create them because I don't know appropritate sizes ( swap size ) and location of swap 0, 1, etc.  For this reason I'm choosing New install on entire disk and also I'm choosing to reformat.  I'm not just continually reinstalling and leaving the old failed attempt partition on the drive.

I can say this much when I installed Windows xp in the past it has installed the main installation to H:  because of built in memory card reader and USB, firewire ports on the front of the PC case.  It's an ideq biostar small FF PC. 

Can I fix this manually since I'm logged on, I hate to turn off the PC without fixing it.  Thanks

---

### Post by KKoudelka on 2010-09-20
I have an idea if all else fails.  I'll unplug all those other devices, like I have done in the past to get windows to install to the C: drive  instead of H:

---

### Post by perspectoff on 2010-09-20
> **KKoudelka said:**
> This is now my eighth attempt at installing this and it now finally booted up.  You are right I don't now about partitioning that's why I choose to install on the entire Disk and reformat.

there are not any other partitions like ntfs

under administration/disk utility 

I see device:  /dev/sda1

type ext4

It shows volumes 77 GB ext4

Extended 3.3 GB
3.3 GB Swap

Nah. That looks correct. I wouldn't change anything. I think you got it right and don't need to edit anything. 

Ubuntu has a readahead feature that records your settings and doesn't always stabilize until two boots. Windows is gone, NTFS is gone.

Yours is probably stable, now. 

If you want to look at your partitions, now, you can install GParted as an app from the Terminal:

 sudo apt-get install gparted

or from Synaptic Package manager (as the package gparted).

Then run it:
 sudo gparted

or from the menu.

You can then see your hard drive and what now appears to be two partitions, correctly installed and of the correct sizes.

With GParted you can also learn a little about partitions (without changing anything) so in the future you can be familiar with this useful tool.

You are well on the way to being a proper Ubuntu Geek! I salute you and proffer the ceremonial Ho-Ho and can of diet Dr. Pepper!

---

### Post by KKoudelka on 2010-09-21
My first cup of Ubuntu is a little bitter.  Naw just kidding I love it my labtop which is dual boot with windows, I never even use Windows on it hardly any more.

I'm still having problems, it might be something wrong with the PC.  I put a new much smaller hard drive in just to test it.  It was an old 8 gb hard drive from an xbox that was reformatted.  I erase all partitions and let Ubuntu manage it for me, the same thing happened.

partition 1 ext4 
partition 5 swap
no other partitions are on the hard drive and this is how it shows up during installation

I started reinstalling before I saw your response because when I turned off the PC it would'nt boot into Linux, I keep gettng errors.

---

### Post by KKoudelka on 2010-09-21
I wound up putting the 80G  hard drive in another computer and installing dual boot windows/linux

It still showed as Partition #1 ext4
and partition #5 swap

even after formatting and everything.  I wound up putting GRUB on the Windows hard drive and it's working fine now. 

I think there is something wrong with my other desktop.  It quit working about a year ago and that's why I stopped using it.

---

