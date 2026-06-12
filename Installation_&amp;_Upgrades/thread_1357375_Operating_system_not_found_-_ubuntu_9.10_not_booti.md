---
title: "Operating system not found - ubuntu 9.10 not booting"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by 2ways on 2009-12-17
Starting a new thread from [http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900) since the original problem seems to have been solved and my problem is a little different.

I won't repeat everything from previous thread except what is useful for context.

I have a Sony Vaio laptop (pcg-frv31) and have switched from Windows XP to ubuntu 9.10.  I installed ubuntu from the CD and reformatted the drive in the process.  I am not running any other operating system on the computer.  Single boot.

The first attempt to install failed as the CD image was not written properly, but after burning the CD again at lower speed, the installation was successful.  At least that is what I thought.

It turns out that when the installation process was completed, the system reverted (without any warning) to running off the CD, and I didn't realize it.  When I rebooted without the CD, I got the message: Operating system not found.

Every subsequent check demonstrates that ubuntu 9.10 is installed on the hard drive, but when booting without the CD, it can't find the installation.  For example, when trying to re-install ubuntu, at the partitioning stage, it tells me that ubuntu is the operating system installed on the partition I am about to reformat.

When booting with the CD, I find that the partition with ubuntu is not mounted, but mounting the partition does nothing because when I reboot, I get the same error and after going back in via the CD I discover that the partition is again not mounted.

At the suggestion of Darko, I have tried re-installing grub 2 (instructions in previous post), in case that was the problem.  The procedure did not generate any errors, but didn't solve the problem.  The result of that was that when I booted without the CD, I got:

GNU GRUB version 1.97~beta4

sh: grub>

I didn't know what to do from there, so I exited the shell, which gave me: Operating system not found.  The odd thing is that, since I have only one operating system on the computer, grub should have simply booted me into ubuntu.

As an aside, before I re-installed grub, grub wasn't actually there.  That is, I didn't re-install it, I installed it.  The /media/'mountpoint'/boot/grub folder was empty, whereas now it is full.  This makes me worry that what I thought was a successful installation of ubuntu was not so successful after all (even though ubuntu thinks it's there, perhaps there are some critical configuration files missing).

Sorry for the long post.  Thanks for the help.

Cheers,
Lewis

---

### Post by darkod on 2009-12-17
In this case, and since this is new installation and you have no data to lose, I would recommend trying to install it again with the good cd. Just boot from the cd, select Install Ubuntu, and at step 4 select Erase disk and use all space, etc.
In case you want to create your partitions manually, if you have questions ask first in order to create them successfully the first time. It's hassle to resize after.
Let us know if the second installation has the same problems.

---

### Post by 2ways on 2009-12-17
Thanks, Darko.

I've now been running the install for the past 4 hours and I have been stuck at 'Configuring apt' and '80%' for an hour and a half.  I'm guessing now I'll never get past 80%.

This is what makes troubleshooting the boot problem so impossible!  I can't just have another go at something since it takes the entire day to just try one solution!

The forums have suggested switching on a swap partition for the Live CD to use during install, but I have a swap partition and it appears to be switched on as well.  Those posts were all several years old anyway for version 7.04.  I presume someone fixed that problem along the way to 9.10.

My laptop has a 2.4 G Celeron chip with 1 G of RAM, so I can't believe it's a question of needing to use the Alternative CD to run the text-based installer.

I have a feeling I'm never going to get my boot problem fixed unless I fix the slowness first.

It also takes over 30 minutes (sometimes up to an hour) to boot to the desktop with the Live CD.

Anybody have any thoughts on this?  I realize this is a different problem from what the thread is about.

Thanks,
Lewis

---

### Post by darkod on 2009-12-17
That sounds awful. And may be part of the problem why you couldn't start the boot after the first install. The spec of the laptop sounds sufficient.
It could be badly burnt cd, so reading it takes ages, or a much worse option, your hdd getting ready to die on you.
Have you considered burning another cd (I know this is your second) or even downloading another ISO image? This one might be corrupted and hence the first cd was also bad, not just because of the burn speed.
Also you could try creating bootable usb stick and use that.

---

### Post by cholericfun on 2009-12-17
30 minutes to boot from cd is a major pain
maybe you can borrow a faster cddrive from someone. alternativly make a bootable USB and try that (from 9.10 LiveCD)

---

