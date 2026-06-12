---
title: "Fresh Install 21.04 Executing ‘grub-install/dev/sda’ failed"
date: 2021-05-26
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2021-05-26
I had an issue with upgrade and then fresh install of 20.10.  Got busy and now thought I could fix it with 21.04

I was able to run the live CD and get to the page Try or install.  (I checked the download was correct with the SHA256SUMS etc)

I have a dual boot Windows and Linux desktop (boots correctly in windows).

I chose the install now and I then get the error.

[COLOR=#000000]Executing ‘grub-install/dev/sda’ failed[/COLOR]
[COLOR=#000000]This is a fatal error[/COLOR]

I did a chkdisk in windows without any errors.

I've seen many post about fixing this, with many different methods. 

Of note, when I boot from the USB, I get an initial grub screen with not the best graphics to choose ubuntu or ubuntu with safe graphics or something like that (never seen that with a live CD before).

D

[COLOR=#000000][/COLOR]

---

### Post by ajgreeny on 2021-05-26
What version of Windows and is it installed using UEFI?
If a pre-installed Windows 10 it will certainly be UEFI but if you upgraded from Windows 7 it could easily be installed in legacy/BIOS mode.

To give us more detailed info see **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the any repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system.

---

### Post by claven123 on 2021-05-26
[https://paste.ubuntu.com/p/tp9BBhzxRG/](https://paste.ubuntu.com/p/tp9BBhzxRG/)

I actually don't remember, but I'm almost certain I upgraded to windows 10.

Bios mode is: Legacy




D

---

### Post by ajgreeny on 2021-05-26
I am not a great expert in reading and decoding the boot-info script output but I note that it appears that you have an EFI/ESP partition on the hard disk.
```
fdisk -l (filtered): ___________________________________________________________

Disk sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk identifier: 0xd283b5ea
      Boot      Start        End   Sectors   Size Id Type
sda1             2048     718847    716800   350M  7 HPFS/NTFS/exFAT
sda2           718848  979328108 978609261 466.6G  7 HPFS/NTFS/exFAT
sda3       1952518144 1953519615   1001472   489M 27 Hidden NTFS WinRE
sda4        979329022 1952518143 973189122 464.1G  5 Extended
sda5  *     979329024  980379647   1050624   513M ef EFI (FAT-12/16/32)
sda6        980381696 1952518143 972136448 463.6G 83 Linux
Partition table entries are not in disk order.
```
How did you create the USB you used to install and was the USB you used for that the same one as you used to run Boot-info script?

Some applications used in Windows will only create a UEFI boot disk I believe, which would mean that you booted the USB in UEFI mode when you installed, therefore Ubuntu will have installed in UEFI mode, which will not work if your Windows is using legacy/BIOS.

Wait for someone who understands the report better than I do before carrying out any further activities.

---

### Post by claven123 on 2021-05-26
I used my other Ubuntu 20.10 only machine to create the USB.

Yes, I made it while in the liveCD session on the USB.

D

---

### Post by grahammechanical on 2021-05-26
Please do not take me for an expert either. This is what I see in the Boot-Repair report.

The drive has an extended partition (sda4). This means the drive has a Master Boot Record (MBR) partitioning scheme. I do not think that there should be an EFI partition (sda5). Indeed there are no boot files in sda5.

I am guessing that this is a BIOS motherboard and not an UEFI motherboard. I am also guessing the Ubuntu install session was in UEFI mode. Boot Repair says

> Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of the same hard drive for core.img. core.img is at this location and looks for (,msdos6)/boot/grub. It also embeds following components:
This is correct. msdos6 = sda6. The location of the Grub boot files. If there was a previous install of Ubuntu on this machine (20.10) it could have put
Grub into the MBR of the drive. This would mean that the installer of 21.04 was accurate when it said that the install of Grub into the MBR failed.

Boot Repair is offering to do the only thing it can do.

> The default repair of the Boot-Repair utility would purge (in order to unsign) and reinstall the grub2 of sda6 into the MBR of sda.
Grub-efi would not be selected by default because: legacy-win no-win-efi 
Additional repair would be performed: unhide-bootmenu-10s win-legacy-basic-fix

Regards

---

### Post by tea for one on 2021-05-26
[COLOR="#0000FF"]Line 72 [/COLOR] 3 Operating systems detected
[COLOR="#0000FF"]Line 105[/COLOR] Windows 10 on sda1 in Legacy mode
[COLOR="#0000FF"]Line 106[/COLOR] Windows 10 on sda2 in Legacy mode
[COLOR="#0000FF"]Line 116[/COLOR] EFI System Partition (ESP) for Ubuntu
[COLOR="#0000FF"]Line 109[/COLOR] Ubuntu on sda6 in UEFI mode

How did you end up with 2 installations of Windows 10?

You have Windows 10 in Legacy mode and Ubuntu in UEFI mode and this is ill-advised, hence the grub installation failure.

In order to future proof your system, you should consider:-

Backup your data
Install both systems in [COLOR="#0000FF"]UEFI[/COLOR] mode with [COLOR="#0000FF"]GPT[/COLOR]
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by claven123 on 2021-05-26
I've had previous Ubuntu going back many, many years.   The last was 20.10 which did not install correctly.  The last that worked correctly was 20.04

I thought the second windows was the recovery area for windows?  When I boot, I only show Windows 10 and Ubuntu 21.04.  I haven't installed a second, just upgraded from 8 to 10 at some time.

I'm not sure what is on sda5

Gparted shows boot, esp as flags for sda5
If I click on information:
Unable to read the contents of this file system!
Because of this some operation may be unavailable.
The cause might be missing software package.
The following list of software packages is required for fat32
file system support: dosfstools, mtools

I'll review that last link "[COLOR=#000000]Install both systems in [/COLOR][COLOR=#0000FF]UEFI[/COLOR][COLOR=#000000] mode with [/COLOR][COLOR=#0000FF]GPT"[/COLOR], do I need to resolve the above issue first?


D

---

### Post by oldfred on 2021-05-26
With BIOS, Boot-Repair copies bootmgr & BCD from Windows boot partition into the main or c:drive partition as many users have removed the boot partition not knowing it is essential. And then they do not have any boot files.
But then grub does search for Windows boot files, not Windows boot flag like Windows uses, to find Windows bootable partitions and it then finds both NTFS partitions as bootable. But Windows only uses its boot loader from primary NTFS partition with boot flag.

But you installed Ubuntu in UEFI mode, and had an old grub in MBR for BIOS boot.
You can tell Ubuntu is installed in UEFI mode from ESP, UEFI boot entry and mount of ESP in fstab. 
You cannot have both BIOS boot Windows and UEFI boot of another system on same drive without major work arounds to change booting.
Windows has to have boot flag on its bootable partition, your sda1 (although now it could be sda2 since boot files copied) and UEFI requires boot flag on ESP - efi system partition. Only one boot flag per drive.

Use gparted and move boot flag from sda5 to sda1. 
Use Boot-Repair to install a Windows type boot loader to MBR ( or Windows repair/recovery flash drive) and make sure Windows boots. Fast start up must be off.
Then use Boot-Repair to install BIOS version of grub to MBR.

Since you only have one MBR, and two systems booting in BIOS mode, you need to always have both Ubuntu live installer & Windows repair flash drive.
Grub only boots working Windows & Windows updates will turn fast start up back on. Then grub will not boot Windows & you have to do the boot loader switches again.

Its a lot easier to have Windows in UEFI mode as then it can be directly booted from UEFI boot menu, if grub does not boot Windows.
Microsoft has required vendors to install Windows in UEFI boot mode to gpt partitioned drive for almost 10 years, so BIOS installs are not recommended.

Note conversion from MBR to gpt partitioning will erase drive so have good backups. But plan on eventually converting both systems to UEFI.

---

### Post by claven123 on 2021-05-26
Ok, sounds like I have a mess (not sure how I got to this point). 

Can I reinstall windows 10 in UEFI in GPT, then install Ubuntu?  

I'd overwrite/erase the entire drive in the process.

Will that fix the issues above?  

D

---

### Post by tea for one on 2021-05-27
Yes to all three questions.

One big advantage of GPT is that you are not limited to 4 primary partitions and it will, hopefully, be easier to manage in the future.

Here are some general observations (some may not be applicable)

[COLOR="#0000FF"]Backup your data[/COLOR]
Both systems in UEFI mode with GPT
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

_UEFI settings_

Disable Secure Boot
Disable Fast boot 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
Disable TPM

_Windows 10_

[COLOR="#0000FF"]Backup your data[/COLOR]
Turn off Bitlocker
Disable Fast Start Up i.e. Windows is not hibernating
Disable applications which manage Intel Optane memory & storage
Disk must be GPT
Install Windows 10 in UEFI mode
Check via System Information > System Summary > BIOS mode > UEFI
Windows will have  an EFI partition (needed by Ubuntu later)
Use Windows tools to reduce Windows partition size and create free space
Reboot Windows to allow chkdsk to run
Windows may need AHCI driver
[https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347](https://discourse.ubuntu.com/t/ubuntu-installation-on-computers-with-intel-r-rst-enabled/15347)

_Ubuntu Family_

Boot into a live session in UEFI mode (how you boot determines the installation mode)
Allow the installer to find previously created free space (or create your desired partition scheme i.e. a separate home partition)
Check wifi, sound, graphics, mouse, keypad etc
Grub will find the EFI partition already used by Windows
Sometimes (although rare) internet connection prevents clean installation

---

### Post by claven123 on 2021-05-28
I want to delete the ubuntu partitions and then convert the HDD to GPT and then change over to UEFI.  (then partition and install dual boot ubuntu)

The issue is what do I do with sda5?
See image, gparted shows it as fat32 with flags for boot, esp

In disk management in windows it shows it as D; Healthy (Active, EFI system partition)
If I look in file manager it has folder: EFI then in that, BOOT and ubuntu 
In boot it has: BOOTTX64.EFI, fbx64.efi and mmx64.efi
In the ubuntu folder: BOOTX64, grub.cfg, grubx64.efi, mmx64.efi and shimx64.efi

Do I delete the sda5 partition?  Along with sda4 and sda6 (which is the location of ubuntu)

D

---

### Post by oldfred on 2021-05-28
If doing new install and have a new ESP - efi system partition the install of grub2 boot loader will create new folders for /EFI/ubuntu & /EFI/Boot and insert a new UEFI boot entry into ESP based on new ESP's GUID/partUUID. Old esp will be obsolete.
Windows install in UEFI mode to gpt drive will use same ESP with /EFI/Microsoft folder for its boot files.
[https://ubuntuforums.org/showthread.php?t=2462726&p=14040458#post14040458](https://ubuntuforums.org/showthread.php?t=2462726&p=14040458#post14040458)
Usually better to install Windows first as in UEFI mode it wants multiple partitions.  But I prefer a somewhat larger ESP, but not absolutely required.

---

### Post by tea for one on 2021-05-28
No need to delete anything.
There is an [COLOR="#0000FF"]essential[/COLOR] need for [COLOR="#0000FF"]back-ups[/COLOR].
Have you done this yet?

The Windows 10 installer will create GPT and the necessary Windows partitions.

Then you proceed to restore your Windows data, check and double-check.
Subsequently, you can create the necessary free space (using Windows tools) for Ubuntu.

---

