---
title: "Trying to install for dual boot/Ubuntu locks up"
date: 2014-08-05
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2014-08-05
I am trying to install Ubuntu 14.04.1 64bit on a Windows 8.1 64bit laptop for dual boot. I made a bootable USB drive with Unetbootin. ISO md5sum is OK. Checking USB drive for defects is OK. I changed grub.cfg to nomodeset. When I boot off the USB, it starts then locks up. See picture. I made another bootable USB drive with Boot Repair in case I need it. It also locks up. UEFI mode is enabled. Secure boot in enabled also as that is what Ubuntu sugguest. Using Windows Disk tools, I have already made a 100mb partition for the  installation of Ubuntu. Searching here and on the internet has not helped.
Laptop specs are:

Toshiba Satellite C855d-S5201
secure boot disabled  <--Note: I tried enabled also 
Boot mode UEFI Boot
AMD Dual-Core E1-1200 Accelerated Processor
AMD Radeon™ HD 7310
4GB DDR3 1600MHz memory

Disabling UEFI will let Ubuntu boot to try it out, but I have to enable it for Windows. Can I disable UEFI and install Ubuntu, then run boot repair, then enable UEFI for dual boot? I do have three sets of full backups of the computer also.

Thanks all
magpie

---

### Post by oldfred on 2014-08-05
Ubuntu cannot install to any partition that Windows creates, it does not do Linux partitions.
You do want to use Windows disk tools to shrink the main Windows NTFS partition and reboot so it can run chkdsk and update for its new size. You may have to turn fast boot off again as Windows likes to keep it on. 

I expect your 100MB is a typo, you mean 100GB? I would partition that as 20 or 25GB as / (root), 2GB as swap and the remaining as /home. You may want to shrink Windows a bit more and create a shared NTFS data partition. Generally smaller system partitions and larger data partitions work, but Windows likes to default to using system partition so it often needs to be a lot larger. And it likes lots of free space inside its NTFS partition to work well. Usually at least 30% is needed, so do not shrink too much.

With the new Windows only Something Else should be used. The installer does not correctly see Windows 8 and may overwrite it. With Something Else you have total control over partitions, but it does require a bit more understanding of what partitions are and what you need for Ubuntu. The detailed instructions on using Something Else cover that.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 300 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4
2. all but 2 GB Mountpoint /home logical beginning ext4
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)

      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
But I suggest using Windows to shink Windows and reboot Windows first. But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

      
 Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

Some other Toshiba, may have similar issues & solutions?

  [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
      
 Toshiba laptop C850 Windows 7 with upgrade to 8 version -  sudodus
[http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025](http://ubuntuforums.org/showthread.php?t=1769482&p=12606025#post12606025)

Video drivers also often an issue.

 [https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection](https://wiki.ubuntu.com/X/Troubleshooting/VideoDriverDetection)
Ubuntu Precise Installation Guide - AMD/ATI
[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Video_Tearing)
Add Hardware Graphics - ATI: After installing ATI Driver: From QIII
[http://ubuntuforums.org/showthread.php?t=2050320](http://ubuntuforums.org/showthread.php?t=2050320)

---

### Post by magpie03 on 2014-08-06
Thanks Oldfred, but Ubuntu locks up and I cannot get to the main install screen. I'll reread everything again to see if I missed something.
magpie

---

### Post by oldfred on 2014-08-06
When you say locks up how. black screen? That is a video issue.
Or are you not able to even get to the first grub menu when booting installer in UEFI mode?

I have nVidia and have to use nomodeset on ever live installer boot and after install until I install proprietary drivers. Not sure if same for AMD or not.
And some systems need UEFI/BIOS settings changed, but that varies by brand/model of system.

You can install in BIOS mode, and use Boot-Repair to uninstall grub-pc (BIOS) and install grub-efi-amd64(UEFI). But I would expect if video issue in UEFI mode you might still have it.
I might try installing AMD's proprietary driver while in BIOS mode and then convert, but do not know if that works.

---

### Post by magpie03 on 2014-08-06
Thanks again oldfred. I am using nomodeset. Please see the picture I posted. It starts loading then locks up. I think I will try with UEFI off them try boot repair. I am using a USB made with Unetbootin but I am going to make a regular DVD and try that also. Your right about the typo in my first post. Iti s a 100GB partition.
magpie

---

