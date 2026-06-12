---
title: "Installing multiple OS' to an external HDD"
date: 2016-03-24
forum: Installation &amp; Upgrades
---

### Post by derek_2 on 2016-03-24
Please bear with me as I make my very best attempt at clearly stating my problem. I had an extra 160GB HDD to put to use and I want to install 3 separate operating systems: Ubuntu, Mint, and Kali (partitioned 30GB, 30GB, and 40GB, respectively). Previously, I had been using a small thumb drive to use a persistent copy of Ubuntu; however, each time I would use Ubuntu, all of my previous work was erased. I want to avoid that by using a larger HDD and keep a user profile on each OS. Is it possible to do this? I had tried creating a multiboot, using YUMI, but so far that does not seem to be the answer.

---

### Post by Bashing-om on 2016-03-24
derek_2; Hello;

Sure it is doable .. However, managing grub in a multi boot environment is somewhat of an art .
```

sysop@1404mini:~$ sudo blkid
/dev/sda1: LABEL="1404mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1404mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1404" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1404mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="ubie14.04std" UUID="345cab2e-22e7-4f89-8781-05cc0f7628a2" TYPE="ext4" 
/dev/sdb2: LABEL="ubie1204" UUID="7dd23297-30ea-417a-8f69-3e2df76f3192" TYPE="ext4" 
/dev/sdb3: LABEL="ubie15.10" UUID="2ec4733f-db40-4db0-aef8-5c54e54085ab" TYPE="ext4" 
sysop@1404mini:~$

```

What have you got installed on the primary hard drive ?
Show us:
```

sudo fdisk -lu
sudo parted -l

```

see then ->
[INDENT][INDENT]we can finger out
[/INDENT][/INDENT]

---

### Post by oldfred on 2016-03-24
Older BIOS or newer UEFI system?

I have multiple installs of Ubuntu on two drives. My older BIOS system had so many old Ubuntu installs, many obsolete as I kept adding 25GB for a new / (root) partition for testing something. I had to turn off os-prober so it would not find the old installs and clog up the grub menu.

I prefer smaller system partitions and large data partition. Last system installed with BIOS will be the grub in MBR that controls booting, so system you expect to use the most should be last to install.
Use gparted to create all partitions in advance, but keep track. Installer does not show labels and I once installed to a new large data partition instead of my planned / partition.

       Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using) 
   Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29): 

I do not know Kali, but someone posted that it is not really intended to be installed, but just run as live install.

---

### Post by sudodus on 2016-03-24
Welcome to the Ubuntu Forums :-)

Yes, it is possible. Much easier in BIOS mode than in UEFI mode, but possible in both boot modes. The following link and links from it will give you some tips:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

Install to the USB disk like you would have installed into an internal drive. I would recommend that you select ***Something else*** at the partitioning page of the installer.

---

### Post by derek_2 on 2016-03-24
I am quickly realizing that. This is new territory for me and I clearly underestimated the task.

```
/dev/disk4 (external, physical):   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *160.0 GB   disk4
   1:                        EFI EFI                     209.7 MB   disk4s1
   2:       Microsoft Basic Data UBUNTU                  30.0 GB    disk4s2
   3:       Microsoft Basic Data MINT                    30.0 GB    disk4s3
   4:       Microsoft Basic Data KALI                    40.0 GB    disk4s4
   5:       Microsoft Basic Data ROOT                    59.3 GB    disk4s5
```

This is the info on one of the disks:  
```
Device Identifier:        disk4s2   Device Node:              /dev/disk4s2
   Whole:                    No
   Part of Whole:            disk4
   Device / Media Name:      DOS_FAT_32_Untitled_10


   Volume Name:              UBUNTU


   Mounted:                  Yes
   Mount Point:              /Volumes/UBUNTU


   File System Personality:  MS-DOS FAT32
   Type (Bundle):            msdos
   Name (User Visible):      MS-DOS (FAT32)


   Partition Type:           Microsoft Basic Data
   OS Can Be Installed:      No
   Media Type:               Generic
   Protocol:                 USB
   SMART Status:             Not Supported
   Volume UUID:              DB1C36E3-89FB-3F31-95A6-C92DDA6D6075
   Disk / Partition UUID:    CC7ADC8F-FCDC-4B2E-B641-53CE9A4D584E


   Total Size:               30.0 GB (29999996928 Bytes) (exactly 58593744 512-Byte-Units)
   Volume Free Space:        26.8 GB (26800537600 Bytes) (exactly 52344800 512-Byte-Units)
   Device Block Size:        512 Bytes
   Allocation Block Size:    16384 Bytes


   Read-Only Media:          No
   Read-Only Volume:         No


   Device Location:          External
   Removable Media:          No
```

---

### Post by derek_2 on 2016-03-24
@oldfred: I agree with you, it makes sense to have larger partitions for data. I will take some time to read through the links you've provided and hopefully find some insight there. I understand the general purpose of grub. What I do not understand about grub, does it use one data partition to dynamically allocate the memory for each OS? In other words, I could reduce the partitions for each OS to less than 8GB each, and create one, shared data partition?

[http://www.dedoimedo.com/computers/u...all-guide.html]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html")
This link has been VERY helpful! I was lost in Linux! He is very thorough in his explanations. If anybody needs a good starting point, I would definitely recommend this site. :guitar:

I will likely just try using 'Something Else' and see where that takes me, as I did not have much luck using YUMI.

---

### Post by oldfred on 2016-03-24
Grub is not UEFI, multiple disk friendly.
I have tried installing to sdb totally with my main working Ubuntu in sda. And even though I select grub to install to sdb, and even during install it says installing to sdb, it overwrites my /EFI/ubuntu on sda. I quickly learned to back up my ESP - efi system partition on sda.

If UEFI you need to use gpt partitioning. And if external or second drive include the ESP as FAT32 formatted with boot flag. If all installs are UEFI they will install to the ESP on sda, not sure about other installs. If you do not have an ESP on sda, grub will not install correctly. 

Is this not a PC, but a MAC? Your list of disks is not typical.

---

### Post by Dennis N on 2016-03-24
Using custom menus is the easiest way to get a "maintainance free" multi-boot system, where you never need to update any menu entries yourself after a kernel upgrade.

Once you get several installed, you will soon appreciate the value in this approach.  

The guide to creating a custom grub menu system:

[https://help.ubuntu.com/community/Grub2/CustomMenus](https://help.ubuntu.com/community/Grub2/CustomMenus)

Note: The "maintainance free" part of the guide (at the end) is applicable for Ubuntu based systems (includes Linux Mint) but there is way to include some other OSes as well if you install everything as UEFI.

---

### Post by grahammechanical on 2016-03-24
> What I do not understand about grub, does it use one data partition to dynamically allocate the memory for each OS?

Grub = GRand Unified Bootloader. It is the standard boot loader for Linux. It does not dynamically allocate memory (storage memory). Not at all. A Linux OS in an 8GB partition would not have much. if any, space for the installation of additional programs. Partition sizes of 8 - 10 GB are fine for simply testing the installation of Linux distributions but not for any useful use of the distribution.

By having a large, perhaps very large partition set aside for Data we are in the useful situation that the data can be accessed by any Linux distribution and a re-install of a distribution or an install of another distribution into that partition will not risk loosing the data in the Data partition.

There is no point creating partitions for Linux in the Microsoft operating system. For then they get a file system (format) that will need to be over-written by the Linux installer. Use Windows tools to create/delete/resize/move Windows partitions and to create unallocated space. Use Linux tools to create/delete/move/resize Linux partitions.

Regards

---

### Post by derek_2 on 2016-03-24
Alright, I think I have a much better grasp of how all of this operates. Thank you all for the insight and I'm really excited about the capability of all this -- if I could just get the darn thing working.

Yes, I am working on a macbook. Is there a reason as to why grub is overwriting sda? I used GPart to partition the drive and effectively install Ubuntu to the drive as stated in this [tutorial]("http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html"), about halfway down the page. I followed each step precisely, installing Ubuntu to sdd2, reformatting the drive to *ext4, *assigning the *root* ('/') drive to this partition. I then assigned my largest partition (sdd5) to *home* ('/home') and reformatted to *ext4*. I was then prompted to create a swap partition which I did using sdd3. The instructions advise using sdd2, since this is where the root folder exists, to install the bootloader. I did all of this and completed the installation. I restarted my macbook, pressing the option key, which allows me to select a boot drive, but my newly formatted hdd was not there.

I know I'm not quite there yet, but when I go to install Mint to another partition, how will *root* ('/') be affected? Will each OS contain its own *root *directory? I know that they will share the *home* directory. And will the bootloader need to be installed to the Mint partition?

---

### Post by oldfred on 2016-03-24
Do not share /home. That often causes issues with different installs.
Better to create a separate /mnt/data partition and keep all data in that partition and keep /home inside each install.

With BIOS you (almost) never install grub to a partition like sdd1, but only to a drive like sdd.
But with UEFI it really does not matter with Ubuntu's version of grub. It will always install to the ESP in sda. If you do not have an ESP in sda, then the grub install fails and you cannot boot. Usually best to then copy /efi/ubuntu from sda to your ESP on sdd so drive is independant. But if external drive UEFI only  boots from /efi/boot/bootx64.efi, so you have to copy files from /EFI/ubuntu on sda to /EFI/Boot on sdd and rename shimx64.efi to bootx64.efi for system to boot. If internal drive it should boot from /EFI/ubuntu in ESP on sda.

Grub does not overwrite sda, it just adds another folder /EFI/ubuntu to the ESP - efi system partition on sda.

I do not know Macs, they are somewhat different than PCs. You may also want to install rEFInd.
 But may be best to see details:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) 

      
 Alternative efi boot loader for UEFI limited systems:
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)

---

### Post by derek_2 on 2016-03-24
the url from the boot-repair (no idea what it all means, but *very*&#8203; cool!!) [http://paste.ubuntu.com/15491565/](http://paste.ubuntu.com/15491565/)

After trying several variations of the install, I am still unable to recognize the drive at startup. My last attempt involved partitioning the drive as follows: /dev/sdd1 is 30GB primary for Ubuntu and flagged boot, /dev/sdd2 is extended to include, /dev/sdd5 of 20GB for second OS, /dev/sdd6 of 30 GB, /dev/sdd7 of 50GB for /home storage (just sticking with this for now, as it was mentioned in the instructions I'm following), and /dev/sdd8 of 4 GB used for swap. I left ~20GB of unallocated storage for the future. It seems like this should be an easy thing to accomplish. 

> [COLOR=#000000]But if external drive UEFI only boots from /efi/boot/bootx64.efi, so you have to copy files from /EFI/ubuntu on sda to /EFI/Boot on sdd and rename shimx64.efi to bootx64.efi for system to boot. [/COLOR]

Is this a glitch in the software when installing Ubuntu to sdd? 

I've create an EFI partition that is ~210MB, which is not near enough space to copy the files from isodevice/efi/boot on sda to /efi/boot on sdd. The size of the EFI folder on sda is 1.1GB, mostly attribute to the boot.iso file. 

This provided additional tips on dealing with a Mac: [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)

---

### Post by oldfred on 2016-03-25
If moving drive to another system, then you must have the EFI partition at beginning of drive.
And if other systems are BIOS you will also need a bios_grub partition.

This would also apply to any external drive:
 Flash drive to boot in UEFI or BIOS - sudodus 
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)
[http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi](http://askubuntu.com/questions/559007/is-it-still-possible-to-install-ubuntu-to-an-external-harddrive-with-uefi)

---

### Post by derek_2 on 2016-03-25
After heading your advice, I created an EFI partition (sdd1) to contain the boot folder containing bootx64.efi. Essentially all this has done is create a live usb using that partition -- which isn't what I was trying to accomplish. After compiling from the EFI partition for the first time, I now see that it has created root directory containing all the folders. Instead of using the 30GB Ubuntu partition (sdd2), it is effectively running entirely from ESP. The mount point of sdd1 is /isodevice. 
> [COLOR=#000000]Grub does not overwrite sda, it just adds another folder /EFI/ubuntu to the ESP - efi system partition on sda.[/COLOR]

---

### Post by oldfred on 2016-03-25
That is just booting live installer. An ESP only has boot files normally, but we make it a bit large in case users want to experiment.

But when you use flash drive to install, it will put a copy of grub's boot files into /EFI/ubuntu on sda. 

Did you just extract ISO to ESP on external drive? A UEFI boot flash drive can be created with just one FAT32 partition with boot flag.
This is not a full install.
 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040)

---

### Post by derek_2 on 2016-03-25
I have since wasted most of the day attempting to resolve this issue. :-({|=    I've run two Boot-Repairs: This one recommended [repairs]("http://paste.ubuntu.com/15505020/"), and this was after they were [fixed]("http://paste.ubuntu.com/15505119/"). I tried booting into the rEFInd boot manager, but now I just receive errors stating it failed to open everything in the /Boot directory. As a result it defaults to OSX. After the repair, the EFI partition (sdd1), contained 2 additional folders: Microsoft containing a boot folder, and Ubuntu containing shimx64.efi. I removed these two folders, leaving the original boot and tools folders hoping that rEFInd would initialize, but it did not. So I feel like I'm back at square one.

---

### Post by Bucky Ball on 2016-03-25
*Thread moved to **Installation & Upgrades**.*

Not related to a desktop environment issue.

---

### Post by oldfred on 2016-03-26
I have not installed rEFInd (yet). Are the tools & drivers in the ESP from it?

External drives only boot from /EFI/Boot/bootx64.efi. But if you installed rEFInd the bootx64.efi may really be rEFInd's efi boot file. 

The copy of grub from the install expects to find a grub.cfg in /EFI/ubuntu, so we have to copy all of /EFI/ubuntu to the extenal drive & then copy again to /EFI/Boot and rename shimx64.efi to bootx64.efi.

 the boot files in sda's ESP, copy all of /EFI/ubuntu
  Boot files:        /EFI/Boot/bootx64.efi /EFI/ubuntu/MokManager.efi 
/EFI/ubuntu/grubx64.efi /EFI/ubuntu/shimx64.efi  
    
Among many files in sdd's ESP, you want this to really be shimx64.efi
/EFI/boot/bootx64.efi

---

### Post by derek_2 on 2016-03-27
> [COLOR=#000000]the boot files in sda's ESP, copy all of /EFI/ubuntu[/COLOR]
ESP partition contains: /boot/bootx64.efi      /boot/grubx64.efi    /boot/drivers_x64/     refind.conf

Useful [source]("http://askubuntu.com/questions/342365/what-is-the-difference-between-grubx64-and-shimx64/342382"), to validate your point that bootx64.efi comes from rEFInd, and not by renaming Ubuntu's shimx64.efi

There is no MokManager.efi. What is MokManager and where do I get it? 

> [COLOR=#000000]Are the tools & drivers in the ESP from it?[/COLOR]
I downloaded the refind-cd zip file from sourceforge. I proceeded to mount the drive while logged into El Capitan, and move the boot files over to ESP of the external ssd, which is flagged as the boot drive. I restarted my macbook holding down on the option key. I booted into the EFI drive, and viola', the rEFInd manager was there along with several booting options: OSX, Linux-grub, Ubuntu. I selected to load Ubuntu, and it appeared that everything was starting to come together. 

It did not. And this has led me into another, very common problem. The error verbatim:

```
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
  -Check rootdelay= (did the system wait long enough?)
  -Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/66f290fd-e6e6-4aa7-a5c7-7370bb1e817a does not exist. Dropping to shell! 
```

I made some changes I found from another [source]("http://askubuntu.com/questions/522903/gave-up-waiting-for-root-device-alert-dev-disk-by-uuid-does-not-exist-drop") by changing the /etc/default/grub by modifying GRUB_CMDLINE_LINUX to include a rootdelay=10. I don't quite understand why it is necessary to add a delay if the drive was recognized after initially selecting to load Ubuntu from the rEFInd window.

---

### Post by oldfred on 2016-03-27
The MokManger is a new keymanager for UEFI secure boot.
Do not think Macs use Secure boot version of UEFI, yet.

---

### Post by ubfan1 on 2016-03-27
I see ARM architecture files, like bootaa64.efi in your pastbin.  Are you running an Intel 64 bit machine?  The default boot loader for external media changes name for the architecture, so for Intel 64, its /EFI/Boot/bootx64.efi, and for ARM it's /EFI/Boot/bootaa64.efi.  Using shim/grub,
I make the boot{arch}.efi file a copy of shim ( hopefully shimx64.efi, if shimaa64.efi??? where would that come from?) and have a copy of grub in the same directory (/EFI/Boot/grubx64.efi  (assuming intel 64 bit).  The grub.cfg file should still be in /EFI/ubuntu/grub.cfg.  All the grub.cfg file does is pull in the full, maintained, grub.cfg file from your release's /boot/grub/grub.cfg file.

  Installing grub manually (not during the install media installation) does seem to work better if you use the new swithces for uefi removable media (--removable).  At least bootx64.efi is set up as grub.   the --uefi-secure-boot switch does nothing (instead of using shim, but bug filed).

Join the bug 1173457 about the wrong ESP being used.

---

