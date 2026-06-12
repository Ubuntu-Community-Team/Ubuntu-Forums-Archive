---
title: "Recovering Ubuntu fails on Boot-repair"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by brendonwp on 2014-09-11
My URL from Boot-Repair is [http://paste2.org/P30XKPWp](http://paste2.org/P30XKPWp)

I have an older PC (Core-2 Duo) with non-UEFI BIOS.  I bought two new hard drives and an SSD to improve performance. I partitioned the SSD in two and installed Ubuntu 14.04 on the second partition.  This installation ran fine.

Then I installed Windows 8 on the first partition on the SSD, and this was fine too. At this stage I could only boot Windows 8, but I thought no problem.

I then used boot-repair from the live CD of 14.04 using the instructions at [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) to try and recover my Ubuntu install.  I ended up booting into a grub command prompt that I don't know what to do with.

Using a Supergrub 2 disk I can see the Windows partition and boot into it, but cannot see Ubuntu?

---

### Post by brendonwp on 2014-09-11
Booted with the 14.04 live disk and ran gparted to look at my partitions.  My SSD logical partition for Ubuntu has a lock icon in the filesystem column? I had upgraded to Windows 8.1 from 8, and Win had set "fast boot" to ON in the process.  Maybe this caused the problem?

---

### Post by oldfred on 2014-09-11
The lock is probably normal. Live installer auto mounts swap if found on hard drive to speed up install, but that then in effect mounts entire extended partition if swap is logical. You can swapoff or right click on swap to unmount it and then lock on extended partition is removed also.

You have nVidia, so you may be booting but having video issues. I have nVidia 9600GT and have to use nomodeset to boot installer and to boot first time or until I install proprietary drivers from repository.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I do not like Boot-Repair's auto fix with multiple drives as it just installs grub to the MBR of every drive. In your case it does not really matter, but make sure you have BIOS set to boot from SSD. 
Also is BIOS set to AHCI?

Nomodeset should get you into system, but in low quality video mode. Then use System Settings Add'l drivers tab to install latest nVidia driver. Eventually our 9 series card will have to use no drive newer than 340.xx as that will be a legacy version for our cards. But Ubuntu does not normally update to just released nVidia drivers and 340.xx just came out.

I also do not suggest a separate /boot for most desktops. You do have to be more careful to regularly houseclean old kernels as eventually /boot will fill up. But you should houseclean kernels no matter how you configure system anyway. I normally keep 2 let it grow to 3 or 4 and then houseclean using  synaptic.

With Windows 8 you must make sure fast boot or always on hibernation is off. It may keep trying to turn it back on as a default setting with any maintenance.

---

### Post by brendonwp on 2014-09-12
Thanks for clearing up the issues with the partition status, Oldfred.  My problem is I am at the grub prompt, not the menu, and I have no idea how to use the command prompt and don't want to mess things up more.  Supergrub always saved my butt before, but it cannot see the Ubuntu partition either.  Will try and unlock the partition as you suggest, and see if that helps.  If not, will try and reinstall grub from the live disk.  Maybe do a windows repair first, as grub seems to play nicely with it.

The Nvidia drivers are OK, but do appreciate that advice too.

---

### Post by brendonwp on 2014-09-12
Messed around quite a bit.  In the end I used the Windows 8 disk to repair the installation from the command line:
[http://www.techspot.com/guides/630-windows-8-boot-fix/](http://www.techspot.com/guides/630-windows-8-boot-fix/)
This allowed me to boot into Windows but not Ubuntu

Then used boot-repair again from the live disk environment to get access to Ubuntu again:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I had to change the default settings to point it at the / partition on my hard drive.  

Somehow Windows disappeared in this process. After running update-grub from the command line in Ubuntu, Windows reappeared in the grub menu and I was sorted!

Note: Using the Terminal Way commands from the live disk shown here DO NOT WORK:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The live disk is designed for installation and not managing the host disks.

---

### Post by oldfred on 2014-09-12
Glad you got it resolved.

I edited incorrect command in help.ubuntu.com site to link to correct set of commands here:
[https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal](https://help.ubuntu.com/community/Grub2/Installing#via_the_LiveCD_terminal)

---

