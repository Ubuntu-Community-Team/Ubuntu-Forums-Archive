---
title: "Windows 8 64 bit in legacy mode with ubuntu 64 bit in legacy mode?"
date: 2013-04-14
forum: Installation &amp; Upgrades
---

### Post by ub100 on 2013-04-14
Hi,

I have windows 8 64 bit installed in legacy mode and I want to dual boot with ubuntu. HDD and optical drive are set to boot in legacy mode. Should I use ubuntu 64 bit and install it in legacy mode, do I only have to insert ubuntu live DVD, install normally and that will be an install in legacy mode? Or should I install with ubuntu 32 bit because everything is in legacy mode?

Cheers

---

### Post by oldfred on 2013-04-14
Whether 32 or 64bit or legacy mode are not totally related. But only 64 bit version currently has the UEFI secure boot capability as only very new computers have UEFI.

If your system is from the last 6 years or so, has over 2GB of RAM and can run Windows 8, you really should only consider 64 bit. It used to be there were a few apps that only ran in 32 bit, but since I converted to 64 bit with 9.10, three years ago,  I have yet to run into one.

With BIOS/CSM/Legacy with Windows you have MBR partitioning and the 4 primary partition limit. So as long as you have one primary left that you can convert to be the extended partition you can install Ubuntu. Best to also create a shared NTFS data partition and not even attempt to write into the Windows system partition, you should set it as read only if you do mount it.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by ub100 on 2013-04-14
Hi,

Thank you for your reply. It is a new system that can run in UEFI or Legacy mode and everything is set to boot in legacy mode. Do I have to do anything in particular to make sure Ubuntu 64 bit installs in legacy mode? Windows 8 64 bit is installed on the only partition the size of the drive, will the partitioning tool when choosing the install Ubuntu alongside Windows 8 option automatically split the partition and I can just drag the divider to allocate space or do I have to shrink the partition I have already to leave unallocated space before beginning the install?

Cheers

---

### Post by oldfred on 2013-04-14
Always use Windows disk tools to shrink the Windows partition. While the installer usually works some have had issues. After the resize reboot Windows several times to make sure it has run chkdsk and made whatever fixes it needs on its new size.

After resize and if you have run lots of updates, that is a good time to make a full image of your Windows to make it easy to reinstall.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)

    
How you boot install media - flash drive suggested is how it will install. So from UEFI/BIOS menu be sure to boot in BIOS/Legacy/CSM mode and not UEFI mode. With UEFI and the new Ubuntu you have two choices.

Then your install should be like any dual boot on one drive with BIOS/MBR or msdos partitioning. If you used Windows to convert a gpt drive to MBR, you will need to use fix parts to also delete the backup gpt partition. Windows only deletes the primary and Linux then sees MBR and backup gpt and gets confused.

       Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

    
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

### Post by ub100 on 2013-04-15
Hi,

Thanks for the info again.

---

