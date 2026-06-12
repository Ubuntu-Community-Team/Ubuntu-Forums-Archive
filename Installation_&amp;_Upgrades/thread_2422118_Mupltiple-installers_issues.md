---
title: "Mupltiple-installers issues"
date: 2019-07-02
forum: Installation &amp; Upgrades
---

### Post by Dirich on 2019-07-02
I was on 17.10 and happened to wish to upgrade. I download 18.04 LTS and...

1. I create a USB installer while on linux, this partitions my pen leaving only 2 MB of the 8GB available as the FAT32 partition...

Why the need to partition in ext, and why 8 GB partition? Seems unneeded to me...

I proceed to install:

2. If I select "install together with 17.10" before touching the partitions the recap says it will modify **sdb partition 7**
3. If I select the option to replace the current install the recap says it will modify **sdb partition 8**

My primary partition is sdb2, my home is sdb3, my swap sdb4, then I have 2 windows big partitions. Why does the auto install tries to install on different partitions when it should use the same one for both replace and side-install? Why does it not specify properly which ones are those (is partition #7 sdb7)? Why does it try to install on a partition that is not the one where the current 17.10 is installed? To be fair, I'm not even sure if I had 8 paritions in total (and I can't check... keep reading).

The autoinstall clearly can't be trusted, so I'll do the usual manual install. Reformat primary, assign swap and specify the old /home to still be /home. Install succeeds, remove pen and reboot:

4. Grub2 doesn't load any graphic or information. I manually have to find which (hdX,Y) is the partition to look for grub, then specify all the necessary instructions to boot ubuntu.

BUT...

5. Cyclic login bug (successful login brings you back to login screen)...

I switched to shell mode and tried to fix things but failed. I can't even get grub2 to remember changes to the config. I give up, it must be some issue with 18.04 triggered by who knows what.

Ok, switch to 19.04, I have no linux available anymore so I download and create the USB booter under Windows 10. I had to reuse the original USB as that's the only one available. Reboot, get to the menu and select to Install Ubuntu (or check integrity, for that matters):

6. The installer won't start, all I get is:

[I][6.081653] sd 0:0:0:0: [sdc] No Caching mode page found
[I][6.081653] sd 0:0:0:0: [sdc] Assuming driver cache: write through
BusyBox v1.27.2 (Ubuntu 1:1.27.2-2ubuntu3) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) mount: mounting /dev/loop0 on //filesystem.squashfs failed: Invalid argument
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs
[/I][/I]
I would argue having an easy to use and reliable installer is the first thing necessary. This brings me back to when I had to switch to other distros because 16.04 installer couldn't deal with my ultra wide screen... Except that was at least comprehensible. This time it's like a sensless nightmare.

Anybody got any clue on what to do?

P.S.
I tried again 18.04 from a windows made usb boot. Same result as 19.04. This means #6 has to do with the creation of the boot ubs from windows.

---

### Post by oldfred on 2019-07-02
What brand/model system?
What video card/chip?
Some have unique issues and may need boot parameters.

Are you booting in UEFI or BIOS boot mode?

Most of the installers use dd to copy ISO to flash drive, since ISO is a hybrid DVD/flash configuration. But that then converts flash drive to be read as a DVD, so no partitions, and often needs first sector erased to be usable to add partition(s) for data. Rest of flash drive is not then usable. But you can create a persistent install, to allow some data to be saved.

       Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Ubuntu install guide - multiple ways to create live installer to flash drive
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
Updates for ISO to USB.
[https://help.ubuntu.com/community/Installation/iso2usb](https://help.ubuntu.com/community/Installation/iso2usb)
Updates -Instructions to make a boot drive, that boots both in UEFI and BIOS mode
[https://help.ubuntu.com/community/Installation/iso2usb/diy](https://help.ubuntu.com/community/Installation/iso2usb/diy)
[https://ubuntuforums.org/showthread.php?t=2299040](https://ubuntuforums.org/showthread.php?t=2299040)

Once you boot live installer, run this to see current configuration.
       
 May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by Dirich on 2019-07-02
I've changed to RUFUS to prepare the usb installer and I've been able to install both 18.04 and 19.04.
I still get the grub2 booting in text mode issue, and if I get past that stage 18.04 still has the login infinite loop issue. I've not had the chance to boot on 19.04 as I need to google more to find how to bypass the grub2 issue on it.

@oldfred:
I am unsure in which mode I boot. My boot order defaults to my sdb drive first, which is where I have linux and its boot loader. I simply let the booting happen. I think Windows10 uses UEFI? My 17.10 installed grub2 and I had no issues at all, unlike with 18.04 and 19.04.
My system is custom: intel processor, asus mobo, an HDD where I install linux and an SDD for Windows10, an Nvidia GeForce 1070. This has not changed since the time I installed 17.10, so I doubt the issue is here (17.10 had grub2 too).
Tomorrow I'll try the live-mode and see to generate the reports you asked for. Thanks.

P.S.
Personally I now would reccomend this for the 'make a working usb installer' part: [https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0)

---

### Post by oldfred on 2019-07-02
What model Asus? I have a Asus Z97, but UEFI settings & configuration have not changed much with newer Asus Intel version.

Have you updated to latest UEFI from Asus. Important for chip based virus fixes. Both Windows & Ubuntu have updated, but all UEFI also need updating.

How you boot install media, UEFI or BIOS is then how it installs.
With my system, even saying UEFI or BIOS/Legacy/CSM only booted in BIOS mode. I had to have it in UEFI only to be able to boot & then install in UEFI boot mode.

To dual boot from grub, all systems must be in same boot mode, all UEFI or all BIOS.

       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

### Post by Dirich on 2019-07-03
My mobo is Asus z170 Progamer.

My BIOS is UEFI. I have no option to select how to boot, so I suppose I'm booting UEFI. I think Windows10 requires it and with 17.10 I had no problems with grub2. I've not updated my firmware since before installing ubuntu 17.10.

The boot repair report is [URL="http://paste.ubuntu.com/p/MvSkZC42r9/"]http://paste.ubuntu.com/p/MvSkZC42r9/

[/URL]

---

### Post by oldfred on 2019-07-03
You booted Boot-Repair in BIOS boot mode.
And have a BIOS grub installed to MBR of sdb and to the PBR - partition boot sector of sdb1. That may have corrupted the FAT32 sdb1 partition which is really the ESP - efi system partition on sdb.
You very rarely install BIOS  grub to a partition and never ever to FAT32 nor NTFS partitions as those partitions have essential file info in the partition boot sector.
UEFI grub is also always installed to a drive, but it puts boot files into the partition seen as ESP.

You also have or had Ubuntu installed in UEFI boot mode as you have UEFI boot files in the ESP on sda. And you have Fedora UEFI boot files on the ESP on sdb.

You need to only boot in UEFI boot mode. You should get two boot modes for Ubuntu live installer.
One clearly UEFI:flash and other flash where flash may be name, label or pmap for booting USB flash drive. 
You may need UEFI settings on and settings to allow USB boot. And if you have updated UEFI, you need to redo settings. I save a list. Some required and some optional.
See screen shots link I posted above for my Z97, yours will be very similar or identical.

You can see if testdisk can undo the install of grub to sdb1's partition boot sector. Testdisk will call it BS - boot sector.

This is for NTFS, but I believe it is the same for FAT32.
       PBR - partition boot sector NTFS must be Windows
[HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)
[http://ubuntuforums.org/showthread.php?t=1926510](http://ubuntuforums.org/showthread.php?t=1926510)
[http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486](http://askubuntu.com/questions/655290/grub-is-not-letting-me-switch-to-windows-8-dual-boot-process-ubuntu-15-04/655486#655486)
As described, testdisk has an option to "Recover NTFS boot sector from its backup"
If Backup BS isn't available, choose RebuildBS, otherwise Windows repairs will not work 
Instructions - see section on NTFS partition boot sector recovery
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
You want to get to this screen:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery)
select [Advanced] instead of [Analyse] and select [BackupBS]
Also check for /boot/grub in addition to /Boot  
    
You may then need chkdsk (from Windows) or dosfsck on sdb1.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sdb1
The -a seems to help in clearing dirty bit
[URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]https://bbs.archlinux.org/viewtopic.php?id=164185

      [/URL] Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
    [URL="https://bbs.archlinux.org/viewtopic.php?id=164185"]
[/URL]

---

### Post by Dirich on 2019-07-08
Thanks oldfred, this clarified a lot.

I've setup UEFI only for the usb boot, then proceded to erase and remake the efi partition, for extra safety (and because its size was 268MB and I much prefer it to be 256MB), and the install was a success (with some problems that are unrelated to this whole booting mess).

I run Windows and its boot loader on sda, with sdb reserved for Linux (and its boot loader) plus FAT32 shared data space. I boot from linux boot loader, which sees windows. I've had issues some 10 years ago with having linux write its boot loader in place of window's one (ended up having to reinstall windows when I reinstalled linux), and windows loader never cared to find my linux installs, so by doing 2 disks 2 loaders and letting grub be my default loader, I avoid any issues whenever I update linux, as I can always boot windows by changing boot order.

---

