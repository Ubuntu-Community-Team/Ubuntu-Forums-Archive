---
title: "Dual Boot / Windows 8.1"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by Jeff_T on 2016-06-01
So, there's no way that I'm ever using Windows 10. I'm going to start using Linux instead. 

I'd like to start being setting up a dual boat with my current Windows 8.1 machine and then getting a dedicated Linux box once I'm used to the new OS. 

Can anyone recommend me a guide for setting up a dual boot for ubuntu?

---

### Post by oldfred on 2016-06-01
If system originally Windows 8, then it is UEFI boot with gpt partitioning. You want to be sure to install Ubuntu in UEFI boot mode to make it easy to dual boot. And how you boot install media is then how it installs.
Make sure fast start up or always on hibernation is off in Windows. Use Windows own partitioning tools to shrink the NTFS partition, but leave at least 30% free space as NTFS slows down greatly if it does not have a lot of space. Reboot Windows immediately to let it run chkdsk and repair to its new size.

Then boot Ubuntu installer, you can use gparted to partition in advance, or just use installer to create partitions. Auto install option only creates / (root) and swap and if a new user just starting out that probably is all you need.

       Ubuntu UEFI install ISO
Also links on how to create a bootable DVD or USB flash drive, from Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Easy way to create UEFI only bootable flash drive
[URL="http://ubuntuforums.org/showthread.php?t=2299040"]http://ubuntuforums.org/showthread.php?t=2299040
[/URL]
 Systems need Windows fast start up (hibernation) and UEFI/BIOS fast boot or quick boot UEFI settings turned off. Vital for some systems. UEFI fast boot may prevent or make it difficult to get into UEFI menu. Some systems need password set to allow settings changes (Acer for one).
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html) 

      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
More info on Windows:
[http://www.eightforums.com/](http://www.eightforums.com/)

More useful links and details in link below in my signature.
 

    [URL="http://ubuntuforums.org/showthread.php?t=2299040"]
[/URL]

---

