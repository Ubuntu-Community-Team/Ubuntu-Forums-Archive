---
title: "How to set up a dual boot with windows 10 and ubuntu 16.04 LTS on Dell xps 15 9550"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by miggy2 on 2016-04-25
Hi,

I've been scouring the internet to find a decent guide in order to install ubuntu 16.04 LTS in dual boot to the pre-installed Windows 10 on my Dell XPS 15 9550 but to no avail.
The Dell Laptop is in RAID and has an SSD (presumably a nvme drive) according to its base settings and from the my order report on Dell's website. I've tried partition my current RAID storage to have some space for Linux, turned off fast start up on windows, and to switched to ACHI mode on BIOS, then tried to install 16.04 LTS but there are no storage drivers shown when prompted the partition section. I know that I've done something wrong between or during those short steps but I am unsure as to how to approach setting up ubuntu.

I need to set up ubuntu for work and dual boot to windows 10 for other miscellaneous things.

If anyone is kind enough to layout the steps in which to set up the system, I'd greatly appreciate it. If need be, I have a Windows 7 OEM to reinstall windows, sadly I don't have Windows 10 OEM disk as of writing this thread. 

Thank you.

---

### Post by oldfred on 2016-04-25
My Dell with Windows 8 and a SFF desktop, made me do both a Windows backup & a Dell backup.

You should also create a repair flash drive.
 Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/) 

      
 Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[http://ubuntuforums.org/showthread.php?t=2317843](http://ubuntuforums.org/showthread.php?t=2317843)
Dell Xps 15 9550  Ubuntu 15.10 on new Infinity display (i7 6gen 16gbr UHD 4k touch) post 272 says 16.04 good
[http://ubuntuforums.org/showthread.php?t=2301071](http://ubuntuforums.org/showthread.php?t=2301071)
[http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241](http://ubuntuforums.org/showthread.php?t=2301071&p=13447241#post13447241)

Do not know about RAID, but with standard drives and NVMe you need to use the very newest version of gparted. But with RAID you generally use the RAID tools not gparted for partitioning.
       
 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[http://gparted.sourceforge.net/index.php](http://gparted.sourceforge.net/index.php)

---

### Post by miggy2 on 2016-04-25
I don't mind getting rid of RAID and switching to ACHI, but is there a way to get back W10 or at least let me download a fresh W7 with ubuntu dual boot? The set up I have has a 32GB SSD cache in RAID and I don't mind setting up the W7 and Ubuntu on the HDD. I've tried doing that but when i try installing W7 through USB, the installation settings don't load.

I've read the article before and I've tried a similar rendition, but I'll try it again! :)

---

### Post by oldfred on 2016-04-25
That configuration is not really RAID, but Intel SRT. 
Several brands used that, so configuration is the same.
If primarily an Ubuntu user you can make the SSD / (root) and have /home or data on HDD.
If primarily a Windows user you probably want to keep the SRT, but it only speeds booting.
Some with the larger 32GB were able to have both as Intel SRT is caching just RAM and most then only use 8GB of the 32 leaving enough for / for Ubuntu.

Have not seen on of these for a while. It used to be Ubuntu would not see the drives at all as standard desktop installer would not see the RAID. Then installer would see RAID, but grub would not install correctly as it is not RAID and grub should be in MBR (if BIOS) not in a RAID partition's MBR.

 Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
HP Envy  Windows 7 with MBR & SRT
[http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx](http://askubuntu.com/questions/159645/dual-boot-installation-of-ubuntu-12-04-lts-on-hp-ultrabook-envy-4-1002tx)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by miggy2 on 2016-04-25
Thank you. I'll read it and work on it!

---

### Post by miggy2 on 2016-04-25
Thank you, will work on it

---

