---
title: "Dual Boot issues"
date: 2013-02-19
forum: Installation &amp; Upgrades
---

### Post by cstambaugh on 2013-02-19
I have searched and cannot find any threads, maybe I missed it so I apologize if this has been asked. I have a Dell Studio laptop and I am running Windows 8 and have been trying to dual boot with Ubuntu. 
I installed ubuntu using WUBI but it looks like it installed inside Windows 8 and the compiz settings were very limited. 
I am sure it is because of the way I installed it, inside Windows.
So I want to dual boot. I have installed 12.04 on a bootable USB made with the directions on the Ubuntu Web site. When I boot into the usb all it does is beep when I try to run it from the stick, and to run the installer. Nothing will run.
 I dont want to burn a DVD disc (no CD's ) and have it do the same thing. 
I also went into the disk manager and shrank the volume. so there is over 100 GB unallocated for an install. The usb installer just will not work. I have done the creation of the disc several times. I used the same method to install Linux mint prior to the Windows 8 install, and was dual booting with Windows 7 and  Linux Mint. I just could not get Compiz to work right so I wanted to try Ubuntu on this second machine I have.
My other machine is running Windows 7 and Ubuntu 12.04. 
Is this an issue With Windows 8? Or am I doing it wrong? Oh these are both 64 bit. 
Chris

---

### Post by oldfred on 2013-02-20
Do you have the new 12.04.2? 

Wubi does not work with gpt partitions and all new Windows 8 systems use gpt partitions as they are booting with UEFI.

Have you turned off secure boot in UEFI and fast boot? 
Are you using the 64 bit version?

       You will need to use the 64 bit version of 12.10 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

It will install based on the mode you boot flash drive either UEFI or BIOS/legacy/CSM mode. 

What video do you have.

Other models of Dell that have eventually worked.
       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS14
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache) - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

### Post by cstambaugh on 2013-02-20
for some reason it just would not work from USB stick. I burned it to a DVD (figured it was a waste of space on a DVD) and it worked like normal. I think there was something with the usb boot penlinux setup.
Thanks for the response!


How do I mark this as answered or solved?

---

### Post by darkod on 2013-02-21
> **cstambaugh said:**
> 

How do I mark this as answered or solved?

Above the first post, Thread Tools, Mark as Solved.

---

