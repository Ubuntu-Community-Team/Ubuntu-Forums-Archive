---
title: "This computer currently has no detected operating systems"
date: 2013-03-14
forum: Installation &amp; Upgrades
---

### Post by EricDallal on 2013-03-14
Hello,

I just bought a (refurbished) computer. I have done almost nothing on it and I would like to install Ubuntu from a live CD disk. However, I am getting the message: "This computer currently has no detected operating systems. What would you like to do?". Windows 8 is installed on the computer and works, but is not being detected by Ubuntu. I have read that this might be a consequence of partition tables, so I have attached a screenshot. What should I do?

Edit: For solution, see link in last post.

---

### Post by oldfred on 2013-03-14
Since it shows an efi partition, it has Windows in UEFI mode with gpt partitioning. 

Was this a system with Windows 8 pre-installed? If so turn secure boot off.

What computer & model is it. Some install without much issue, some have issues, and some may not install or require major effort.

 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by EricDallal on 2013-03-14
> Was this a system with Windows 8 pre-installed? If so turn secure boot off.
Windows 8 was pre-installed. I will look up how to turn secure boot off.

> What computer & model is it. Some install without much issue, some have issues, and some may not install or require major effort.
It is a Dell Inspiron 17R SE Laptop Intel i7 Quad-Core 2.4GHZ - 8GB Ram, 1TB HD.

> You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
My live CD has the 64 bit version of 12.04.2. What does it mean for quick boot / fast boot to be turned off? Will my computer start up more slowly? I actually have no idea what the efi partition does. The Windows partition has a 30GB operating system on it. How do I back that up?

> Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
My usual Ubuntu installation consists of having a NTFS windows partition and an extended partition containing an ext3 partition for Ubuntu, a swap space partition, and a (shared) FAT32 partition for data.

> As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3. Details:
So how do I do that?

---

### Post by oldfred on 2013-03-14
Both 12.10 and 12.04.2 have the new shim file to install in secure boot systems. But some still will not work as they have modified UEFI to only boot the Windows boot efi file. Boot-Repair has a work around that renames the grub shim file to be the Windows file. Since shim has the Microsoft key it still works. And then grub's menu chain loads to the backup of the original Windows efi boot file.

With gpt partitioning you do not have an extended partition nor any logicals. The new limit is 128 partitions with gpt, but even that can be changed.

Several other Dell systems. UEFI may be similar with only differences for the different hardware configurations.

 Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell XPS 14 Ultrabook what works
[http://ubuntuforums.org/showthread.php?t=2116597](http://ubuntuforums.org/showthread.php?t=2116597)
 HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)
Dell XPS13 general info mega-thread
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Dell XPS 8500, desktop. Win 8 eventually worked (Ignore sidetrack to EasyBCD)
[http://ubuntuforums.org/showthread.php?t=2086383](http://ubuntuforums.org/showthread.php?t=2086383)

---

### Post by EricDallal on 2013-03-14
Thank you for your help. I have been following the instructions from one of the links you posted. Specifically, [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI").
Step 2 requires entering the BIOS. I did some research on-line and found this: [http://www.makeuseof.com/tag/how-to-access-the-bios-on-a-windows-8-computer/]("http://www.makeuseof.com/tag/how-to-access-the-bios-on-a-windows-8-computer/"). I followed the directions to reach the Advanced Settings menu, but there is no UEFI firmware settings submenu. The article states "If you don&#8217;t see the UEFI Firmware Settings tile here, your computer doesn&#8217;t use UEFI". Is it possible that the computer doesn't actually use UEFI? Perhaps it once did, but the OS was re-installed by whoever refurbished it and now it doesn't? Whatever the case, I don't seem to have access to the BIOS.

---

### Post by oldfred on 2013-03-14
Each vendor's UEFI is different. But all systems with Intel i-series chips have motherboard with UEFI and CSM of legacy BIOS mode.

You have to have BIOS/UEFI. Some have early versions that look just like BIOS, but have another setting for UEFI on or off.  IF system had Windows 8 pre-installed then it has UEFI with secure boot as that is a Microsoft requirement.

---

### Post by EricDallal on 2013-03-14
I was able to confirm that the system does boot in UEFI, although I'm still not sure how exactly to access the BIOS. The article I' following suggests that it should be possible to install Ubuntu alongside Windows, but I still have the problem that Ubuntu isn't detecting Windows. Do I need to try a different version of Ubuntu (I tried 12.04.02)? Also, I was reading in articles that the problem about Ubuntu not detecting Windows is sometimes caused by having overlapping partitions (or something along those lines). I can't remember the post, but it was on these forums (I was in Windows on my old computer and the computer crashed). It said to install gdisk and try that. gdisk did indeed complain about overlapping partitions.

---

### Post by cruizer04 on 2013-03-14
Goto that annoying side bar that windows 8 has, at bottom click click Settings, then again at the bottom click Change pc settings, then click General from that menu, then scroll down to the bottom and you will see Advanced Start up and click Restart, then i think it says UEFI and click that and it will take you to your Bios....If that doesn't work for you, there are like 2 other ways, Restart and hit F2, or goto Power and hold shift then click Restart. Good Luck!

---

### Post by EricDallal on 2013-03-15
Well, it took a while and I wasn't able to get things working with secure boot on, but I think everything now works. I'm a bit miffed at the Ubuntu partition tool though, as it gave different sizes than what Windows gave me. With my experience, I trusted Ubuntu during the installation process and proceeded to shrink the Windows partition further. When I restarted and opened gparted, I found that Ubuntu was now in agreement with Windows about partition sizes. The result is that my OS partitions (both Windows and Ubuntu) are smaller than I would have liked them to be. Hopefully it won't be a problem down the line.

The solution I found was indicated here: [http://ubuntuforums.org/showthread.php?t=2108450]("http://ubuntuforums.org/showthread.php?t=2108450")

A few notes: I didn't need to disable Intel (R) Smart Connect Technology and Intel (R) Rapid Start Technology.
I also installed Ubuntu 12.04.2, rather than 12.10, as is recommended in the tutorial. I hope this helps anyone who runs into the same problem. I presume that this will become more and more common. Thank you cruizer04 and especially oldfred for the helpful advice.

---

