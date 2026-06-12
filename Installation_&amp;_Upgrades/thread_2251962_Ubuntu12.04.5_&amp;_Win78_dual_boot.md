---
title: "Ubuntu12.04.5 &amp; Win7/8 dual boot"
date: 2014-11-08
forum: Installation &amp; Upgrades
---

### Post by risva on 2014-11-08
Hello all,

The problem/querry i post here is seemingly common dual boot issue....but i post here, my typical case....requesting for help!

the fdisk -lu and parted -l output are as under:

```


sudo fdisk -lu
[sudo] password for risva: 

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   976773167   488386583+  ee  GPT
Partition 1 does not start on physical sector boundary.


************************************************************************************************************

sudo parted -l
Model: ATA ST500LT012-1DG14 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   21.1GB  20.6GB  ext4
 3      21.1GB  46.1GB  25.0GB  ext4
 4      46.1GB  96.1GB  50.0GB  ext4
 5      96.1GB  296GB   200GB   ext4
 9      296GB   346GB   50.0GB  ext4
 8      346GB   446GB   100GB   fat32                 msftdata
 7      446GB   496GB   50.0GB  fat32                 msftdata
 6      496GB   500GB   3998MB  linux-swap(v1)




```

i presently have ubuntu 12.04.5 installed in UEFI, the distr is as under:
25GB root / in /dev/sda 3
50 GB partion /dev/sda 4 serve as /home
200GB (sda 5) as linArchive
sda 2 is for future linux installation
sda 9 for backups
sda 8 has been mounted as /Windows (would serve as D:/ drive for windows installation)
sda 7 is for Windows installation
sda 6 swap

now i need to install, Win7/Win8 depending upon feasibility/ interoperability.

BIOS is in legacy support, UEFI boot first mode.

i'm not sure whether windows will be installed in UEFI or legacy.

i want to retain dual boot control with GRUB.

i have taken an image of my present ubuntu installation using clonzilla in /dev/sda9.

Please suggest, how to go about the installation.

PS: machine: Lenovo G50-45 80E300GYIN, AMD A8 6410 proc, RADEON M5 graphic, 4GB RAM.

---

### Post by yancek on 2014-11-08
My understanding is that if you have one system (Ubuntu in this case) installeld UEFI, then the other systems you install need to be UEFI also.  You should install windows 7 first then windows 8 since windows bootloaders are backward compatible.  I'm not really sure how important this is as I believe 8 and 7 use the same boot files but there may be some changes so I would think the safer option is install 7 before 8.  Windows 8 should detect the windows 7 system.  In re-reading your post, it isn't clear that this is what you want.  Are you planning to install both 7 and 8 or either 7 or 8.  The only partition you mention for windows is sda7.  Windows usually needs to be on a primary partition, at least its boot files do which may work as you have the EFI partition on sda1.

---

### Post by oldfred on 2014-11-08
Windows only boots from gpt partitioned drives with UEFI.
How you boot installer is how it installs, so you must boot installers in UEFI boot mode.
If you boot Windows installer in BIOS mode it will convert drive to MBR and destroy the gpt partitioning.
This is why it is generally better to install Windows first, so it can auto create its own partitions and not have to worry about overwriting other system. Or install Windows in UEFI mode to another hard drive in system.

Windows will not install to FAT32, and requires some additional partitions. One small unformatted reserved before the first NTFS as well as the efi. Windows & Ubuntu  will share the efi partition.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

      
  You cannot use the Win7 DVD in UEFI mode, you need to use BIOS mode or modify to USB with UEFI.
Install Windows efi to new drive.
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)
[https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB](https://gitorious.org/tianocore_uefi_duet_builds/pages/Linux_Windows_BIOS_UEFI_boot_USB)

   Convert Windows BIOS to UEFI - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI](http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI)

---

### Post by risva on 2014-11-08
Thanks Yancek (for reply)!

i'm looking for only one Windows installation (either windows 7 or 8), but i'm not sure which one because:
    - i m not sure if windows 7 will install on GPT partition,
    - i believe windows 8 dual boot might be messy because of its restricted boot feature, but would be better supported OS 
    - lenovo provides driver support for both windows version;

Therefore, i request you to suggest windows version as well, license should not be a issue....as it is Ubuntu is my primary OS! 

My restriction is, i don't want to loose my Ubuntu 12.04.5 installation. it has number of updates, third party installs....also i prefer using latest BIOS technique(UEFI) to permit unlimited primary partitions, future support, etc.

I'm open to any (guided) backup and restore option for my Ubuntu 12.04.5

---

### Post by risva on 2014-11-08
.....trying to comprehend what Oldfred just told.....it's a bit too crypted for me....will come back after seeing the references!

---

### Post by risva on 2014-11-08
Hello Oldfred!

what i understand from your suggestion is that:
   - i'll need to make a UEFI USB for Win7
   - backup ubuntu partion in some way on some ext drive ??
   - do a fresh install of windows using UEFI-GPT
   - restore Ubuntu partition from backup  ??

In case i understand you correctly, then i've some more questions :
   - if i copy the ubuntu backup taken using clonezilla on /dev/sda9 to ext HDD....will i be able to use it for restoration?
   - is it worth the effort(especially time) involved in finding ans to all these questions vis-a-vis fresh installation.

---

### Post by oldfred on 2014-11-08
I always suggest backups. 
I backup /home, parts of /etc and list of installed apps so I can do a new install and restore to as it was. Also backup efi partition.
 And always best to have good backup before any major system change. Often it works and even those of us who know better often jump in and make changes and an oops happens. Sometime it seems that system knows you did not make backup so then it hiccups. But if you have good backups it usually works. :)

But you should be able to installs Windows 7 or 8 or 10 to partitions that you create later on drive. It just is that you need all the expected partitions that Windows wants for it to work correctly. See Microsoft links.
And you must create a UEFI bootable install flash drive and boot it from UEFI/BIOS in UEFI mode.

I have not installed Windows in UEFI mode, but links above show how to create a Windows 7 UEFI installer. I believe the newer versions will install in UEFI or BIOS without modification.

This is current but before my UEFI install so I now include efi partition.
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
      
 More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

Others prefer image backups:
      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by risva on 2014-11-17
Hello Oldfred,

i have finally achieved this much:
   - have upgraded to 14.04.1 (installed in efi mode)
   - installed Windows 8.1 in sda7(partitions as mentioned above),
   - used boot-repair to update grub.
  

but boot-repair did some work, but finally reported error and exited. presently grub is showing only Ubuntu as boot option, windows is there but inaccessible.


the repair-info ref given by boot-repair was....http://[paste.ubuntu.com/9052743]("http://paste.ubuntu.com/9052743")

i tried running boot-repair 2nd time; it gave same summary, some error and repair-info ref .......http://[paste.ubuntu.com/9052790]("http://paste.ubuntu.com/9052790")


please help me repair grub, such that i can boot either in linux or windows.

---

### Post by oldfred on 2014-11-17
System does not have an efi partition. You seem to have sda1 &  sda8 as a FAT32 partitions.
Generally the efi partition should be the first partition or near front of drive. Not sure how far into drive it can be.

You need to change the sda1 from bios_grub to efi. You can easily do that with gparted from live Ubuntu installer and click on sda1 and right click set flags. The actual setting for the efi partition (or bios_grub) is a very long GUID, so the boot flag is just one of several shortcuts to assign the correct GUID.

If the efi boot files are in sda8, the copy to sda1. The efi files do not need specific install if backed up or copied. Although each system has to installs its efi boot files into its folder in the efi partition.

Then see what boot repair shows. 
Currently because it does not see efi partition it did not reinstall grub and report did not show what was in the two FAT32 partitions as either one is not shown as the efi partition.

---

### Post by risva on 2014-11-18
the sda1 was earlier the efi partition.

 in my first attempt to  repair from boot-repair cd...because of some problem i had to terminate  the repair,midway....i believe the error is because of that...
second  time i ran the boot-repair, it asked me to put that bios_grub  flag.....then proceeded to do something.....and finally gave the error  report and summary.

this time i booted from boot-repair live cd  and used gparted...it does not have efi option in flags link...so i (out  of instinct) choose 'boot'. boot-repair has given a new refrence file  this time....[http://paste.ubuntu.com/9071745](http://paste.ubuntu.com/9071745)..
also, while executing  gives two pop ups...first one says efi detected....second one says 'you  have booted in legacy mode, you may want to boot in efi mode before  proceeding'...but i have to chosse to proceed in legacy mode  only(because if i change boot options to UEFI only, it does not  recognise the cd(is the cd written incorrectly)).

system is continuing to boot in linux without any problem, but windows option is not there in grub menu.

please advice further action.

---

### Post by oldfred on 2014-11-18
If Boot-Repair is asking for a bios_grub partition that is because you are reinstalling grub in BIOS boot mode not UEFI. Boot-REpair can convert an install from BIOS to UEFI or from UEFI to BIOS.

How you boot installer and Boot-Repair is the default UEFI or BIOS mode, but in advanced options you can force change to other version of grub (and change a few settings) to boot in other mode.

You only show efi boot files, not a grub installed to MBR, so you are in UEFI mode.

If Ubuntu is booting, run this. It only works if grub is in same boot mode as Windows.
sudo update-grub

---

### Post by risva on 2014-11-18
Hello Oldfred,

on updtae-grub, it found windows entry and updated. 

when i reboot...i found 'windows boot manager at /dev/sda1' as an added option in the grub list.....however, if you click on it screen goes blank for split second and comes back at the same menu (probably, the location which should be pointing to windows is pointing back at ubuntu....Ubuntu fan!! yeah).

---

### Post by oldfred on 2014-11-18
Grub only boots working Windows. And Boot-Repair can only make minor repairs to Windows.

Normally Windows correctly installed takes over and you have trouble booting Ubuntu. And the Windows boot files are in the efi partition, so that grub boots Windows from sda1 is correct.

Can you boot Windows directly from a Windows entry in UEFI menu or one time boot key?

You can boot summary report from Boot-Repair to see if Windows in general looks ok, but we cannot really fix Windows issues from Linux.

---

### Post by risva on 2014-11-20
"Can you boot Windows directly from a Windows entry in UEFI menu or one time boot key?"

when i try to boot windows from uefi menu it brings me to grub boot option screen( i believe location which was suppose to have windows partition addr, has been replaced with grub addr).

....as an after thought, if i try a clean dual boot; i still have a query:

  i am not able to boot from cd/dvd(boot-repair 64bit, win8.1 64bit) in UEFI mode. the UEFI menu does not show ODD; ODD is visible only in legacy-compatibility mode.....is there anything i can do to boot from cd/dvd in uefi mode.

---

### Post by oldfred on 2014-11-20
There may be another UEFI setting to allow UEFI boot from external devices. Some hide that behind other menus or even require you to set a password to see that option. If you do have to set password never ever lose that.

Did you run Boot-Repair before. Its work around for the many UEFI systems that internally modify UEFI to only boot Windows was to rename the Windows file and make the Windows file be grub. Then UEFI thinks it is booting Windows but really boots grub. The disadvantage of that work around is that you can only boot the renamed Windows file from grub menu. Other work arounds now are better. And the grub2 os-porber now finds the Windows entry in the efi partition, but that just boots grub again. You have to use the entry that is the renamed Windows file.
But really need to see summary report from Boot-REpair and best if booted in UEFI mode.

---

### Post by risva on 2014-11-21
Thanx Oldfred,

my system now allows dual boot from grub.

what i did was:....reinstalled windows8.1......after complete win installation, disabled secure boot, restarted.....in uefi menu, made the ubuntu entry as first priority, thats it!!

now laptop boots in efi mode to grub, which offers me following:
  Ubuntu
  Advanced Ubuntu
  .efi mokmanager
  windows
  sys setup


i am glad, ubuntu, adv ubuntu, windows, sys setup work as expected!! (Hail Ubuntu forum!!) Many thanks to our moderator, Oldfred!!

please tell what is mokmanager.

---

### Post by oldfred on 2014-11-21
Glad you got it working. :)

I would include in your backup procedure, backing up the efi partition.

Mok manager is the key manager. Currently Canonical paid the one time fee of $100 to use the Microsoft signing key. So you can boot Ubuntu from a Windows secure boot system. But UEFI allows multiple keys and there is a long involved procedure on creating and managing keys.  Do not know details myself.
But then it Microsoft revokes it key there will be a way to create your own key or install a new key from Ubuntu.

       [http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/](http://www.zdnet.com/torvalds-clarifies-linuxs-windows-8-secure-boot-position-7000011918/)
 the whole UEFI thing is more about control than security

---

### Post by risva on 2014-11-25
thanks oldfred!!

---

