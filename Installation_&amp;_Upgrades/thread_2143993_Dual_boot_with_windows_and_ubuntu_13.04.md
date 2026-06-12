---
title: "Dual boot with windows and ubuntu 13.04"
date: 2013-05-10
forum: Installation &amp; Upgrades
---

### Post by Fred4106 on 2013-05-10
I have been using Ubuntu 13.04 as my computers only OS for about a 1 1/2 months, and am loving it.  I just finished building my new computer, and other than installing Ubuntu 13.04 (just to make sure everything was working properly, i reformatted that drive.  Now i want to setup a dual boot with windows 7 and Ubuntu 13.04.  Last time i did this (old computer) i ended up with a bunch of random (seemed like that to me) partitions.

Is there any guide to installing both windows 7 and Ubuntu on the same hdd from start to finish.  All the tutorials i find are for adding Ubuntu 13.04 with an existing win 7.  I need to know what settings i need to use when installing/setting up win 7.

Last time i tried this, i got errors when i tried to boot into win 7, but Ubuntu worked fine.  When i tried the fix i saw on the internet, i ended up having to reformat the hdd.  
Any help would be appreciated, thanks.

---edit---
I want to know exactly how to setup the partitions.  My hdd is 750 gigs, and i would like 150 if that to windows, and whatever else i can use to Linux.  I want Linux to be the primary OS if possible.

---

### Post by oldfred on 2013-05-10
Are you starting from scratch or totally reformatting drive? 
You mention new computer. UEFI or BIOS or do you care? 
MBR is only 30 years old but well understood. UEFI is newer, actually about 10 years old, but not used a lot until with Mac when Apple started using Intel and now Windows 8. Some Windows 7 were also UEFI and even Vista 64 can be UEFI.

Windows 7 normally installs to two partitions a small 100MB boot/repair and the main install with MBR. If you have a new computer and want UEFI you have to convert Windows install to flash drive and add UEFI capability.

If you install Windows in BIOS/MBR you have to be sure to boot Ubuntu installer in BIOS mode to have it install in BIOS. UEFI should give two boot choices one UEFI and the other BIOS/CSM/Legacy. Both Windows & Ubuntu have to be the same either BIOS or both UEFI.

If you decide on UEFI or BIOS we can suggest partitions and install procedures.

       MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

    
Windows only boots UEFI with gpt partitioning and only can use gpt with UEFI. Ubuntu can boot BIOS or UEFI from gpt or BIOS from MBR partitioning.
       ExtremeTech article on what UEFI is,  from 2011 
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)

---

### Post by Fred4106 on 2013-05-10
I am installing everything on a completely blank hdd.  It had Ubuntu 13.04 on its own just long enough to make sure i built the system right.  Then i reformatted the hdd and it just shows up as one lump of free space now.  I would like to install both as bios just because i have no need for any of the new features offered by UEFI. How do insure that both windows and Ubuntu install with the BIOS option?  Exactly what order do i put the partitions in. (Ive been told that matters).

Windows is 64bit ultimate if that matters.

Thanks

---

### Post by oldfred on 2013-05-10
I would just instal Windows. It will use its two primary partitions. I would then shrink it using Windows Disk tools to the size you want. You can partition for Windows in advance, if you want, but it needs a NTFS formatted partition with the boot flag. You can then install into one partition if you desire.

Then make the entire rest of the drive one extended partition and install Ubuntu. My standard suggestion below. You really should have the shared NTFS data partition and set the Windows 7 system partition as read only from Ubuntu.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

I do prefer to install Windows to one hard drive and Ubuntu to a different hard drive if you have two drives.

 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)
Install 12.04- side by side auto install with screen shots
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

