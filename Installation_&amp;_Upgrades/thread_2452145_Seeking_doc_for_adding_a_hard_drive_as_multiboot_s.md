---
title: "Seeking doc for adding a hard drive as multiboot system"
date: 2020-10-17
forum: Installation &amp; Upgrades
---

### Post by satimis on 2020-10-17
Hi all,

Configuration of PC
Drive-a PCIe 3.0 SSD 1TB - OS Ubuntu 20.04 Gnome desktop
Drive-b WD 4TB hard drive for storage
RAM 32G

Now I'm prepared adding a 120G SSD drive for installing Windows 10 to this PC as a multi-boot system. Please advise where can I find the relevent step-by-step instruction.  I don't expect making a mistake to over-write Drive-a.

Thanks in advance.

Regards

---

### Post by oldfred on 2020-10-17
Disconnect drive a & b. If not disconnected, Windows will install to device that is default in UEFI/BIOS. And Windows does not correctly see Linux partitions, so may overwrite a Linux install.
Be sure to install in UEFI boot mode if system is newer and Ubuntu install is UEFI.
Windows has required vendors to install in UEFI boot mode with gpt partitioning since Windows 8 released in 2012. But users could install in the old BIOS/CSM/Legacy boot mode, more for compatibility with old Windows 7 hardware.
How you boot install media is then how it installs. So boot installer in UEFI mode.

Windows will reset UEFI to make Windows first in boot order. You can use efibootmgr or your UEFI to change boot order if you want Ubuntu first in boot order.
You may need to use efibootmgr to readd Ubuntu entry or reinstall grub which uses efibootmgr to add UEFI boot entry. Many UEFI "forget" a Linux boot entry when a drive is disconnected, but seem to find Windows without issue.

Check entry is there.
sudo efibootmgr -v 
sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected)
Also shows NVMe example:
[https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](https://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)
See also 
man efibootmgr

After both installs updated & working from UEFI boot, you can add Windows to grub menu.
sudo update-grub
But Windows fast start up must be off or grub will not find, nor boot Windows.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)
[http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions](http://askubuntu.com/questions/843153/ubuntu-16-showing-windows-10-partitions) &

---

### Post by satimis on 2020-10-17
> **oldfred said:**
> Disconnect drive a & b. If not disconnected, Windows will install to device that is default in UEFI/BIOS. And Windows does not correctly see Linux partitions, so may overwrite a Linux install.

Hi,

Thanks for your detail advice.

I'll perform the test on a spare PC first, not on my daily working PC.

> 
Be sure to install in UEFI boot mode if system is newer and Ubuntu install is UEFI.
Windows has required vendors to install in UEFI boot mode with gpt partitioning since Windows 8 released in 2012. But users could install in the old BIOS/CSM/Legacy boot mode, more for compatibility with old Windows 7 hardware.
How you boot install media is then how it installs. So boot installer in UEFI mode.

On booting the screen will pop-up```

Press DEL or F2 to enter UEFI BIOS

```

Do I need to install UEFI boot mode in the system?

If YES whether I can follow below article;
How To Dual boot Windows 10 and Ubuntu
[https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/](https://www.pcsuggest.com/dual-boot-windows-10-and-ubuntu-uefi/)

Thanks

Regards

---

### Post by yancek on 2020-10-18
If you can, I would suggest that you do as oldfred recommends and physically disconnect the current disks before attaching the device upon which you want to install windows.  Given the info you posted originally, it it pretty certain to be an UEFI system.  Take a look at the Ubuntu documentation at the link below which gives a lot of information on dual booting windows/Ubuntu UEFI though not strictly applicable to your situation as you are installing windows after Ubuntu.  It does have detailed information on UEFI and explains how you can tell if you are booting the install media in UEFI or Legacy mode.

 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-10-18
For UEFI boot of Windows or Ubuntu you must have the 64 bit versions and must boot live installer in UEFI mode. Windows only installs in UEFI mode to gpt partitioned drives. Either drive must be blank or already gpt.
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

Windows in BIOS mode, is known to rewrite partition table (which is required) but "forget" to include any Linux logical partitions when using MBR(msdos) partitioning on same drive. But it also defaults install to boot device in UEFI/BIOS and has overwritten the beginning of the default boot drive with its boot partition. 

With one drive and BIOS recommendation has always been to install Windows first as it requires primary partition(s), Ubuntu does not.
With UEFI not as critical which is installed first.
And with separate drives should not matter at all, as long as you make sure Windows only installs to drive you want. And only way to be sure is to make that the only drive in system during install.

---

### Post by satimis on 2020-10-18
Hi oldfred,

Performed following steps on a spare PC```

AMD 8-core CPU
32G RAM
OS Ubuntu 20.04 on 2TB SSD drive
Storage - WD 2TB hard drive

```
1. Unplug all hard drives
2. Connect an old 128G SSD drive which has Ubuntu 18.04 been installed previously
3. Boot Windows10 Home USB installer
4. Install Windows10 Home
5. Select the driver to be installed
Warning:```

No device drivers were found.  Make sure that the installation media contains the correct driver, and then click OK

```
I was stuck here, having spent an hour without a solution.

Following document didn't help me out.
Fix: No Device Drivers Were Found
[https://appuals.com/fix-no-device-drivers-were-found/](https://appuals.com/fix-no-device-drivers-were-found/)

Please help.  Thanks in advance

Regards

---

### Post by oldfred on 2020-10-18
Did you boot in UEFI boot mode?
Is drive gpt, Windows in UEFI mode will not like an old MBR drive.

I always use gparted to make a new drive as gpt. You have to do that first as for smaller drives it still defaults to MBR(msdos).
Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it.
Or:
sudo parted /dev/sdX mklabel gpt  # where sdX is your drive. Note all data will be erased
Or:
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Did you erase drive or create gpt drive with the required Windows partitions per link in post #5. Easier just to let Windows do its own partitioning.

---

### Post by satimis on 2020-10-18
> **oldfred said:**
> Did you boot in UEFI boot mode?
Yes, there are 2 options```

KingstonDT 101 II
UEFI KingstonDT 101 II

```
1st option - unable to boot
2nd option - able to boot but stopped as reported on my previous posting

> 
I always use gparted to make a new drive as gpt. You have to do that first as for smaller drives it still defaults to MBR(msdos).
Use gparted and select gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... Or if drive is blank or you want to erase it.
Or:
sudo parted /dev/sdX mklabel gpt  # where sdX is your drive. Note all data will be erased
Or:
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

Performed following steps;

Boot the PC with an Ubuntu USB boot stick

On Terminal
$  sudo fdisk -l
```

Disk /dev/loop0: 1.5 GiB, 1601015808 bytes, 3126984 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: F2920917-D23E-4211-A51B-B41061766731

Device       Start       End   Sectors   Size Type
/dev/sda1     2048   1050623   1048576   512M EFI System
/dev/sda2  1050624 250068991 249018368 118.8G Linux LVM

Disk /dev/sdb: 15 GiB, 16028532736 bytes, 31305728 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6fee4eb0

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 3251199 3251200  1.6G  0 Empty
/dev/sdb2       3221944 3226935    4992  2.4M ef EFI (FAT-12/16/32)

Disk /dev/mapper/ubuntu--vg-root: 117.8 GiB, 126466654208 bytes, 247005184 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

Disk /dev/mapper/ubuntu--vg-swap_1: 980 MiB, 1027604480 bytes, 2007040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```
(Remark: this is an old drive.  Its data can be erased)

Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
......
Disklabel type: gpt

> 
Did you erase drive or create gpt drive with the required Windows partitions per link in post #5. Easier just to let Windows do its own partitioning.
No.  This old SSD drive is still working.  I can boot it to Ubuntu 18.04 desktop

How to do it?

---

### Post by oldfred on 2020-10-18
Gparted does not work on LVM. I do not know LVM, but you have to use LVM tools to remove LVM, then if partition is empty, gparted should let you erase drive.
Or maybe other tools will work?

Windows wants either unallocated space or blank drive.

---

### Post by satimis on 2020-10-18
> **oldfred said:**
> Gparted does not work on LVM. I do not know LVM, but you have to use LVM tools to remove LVM, then if partition is empty, gparted should let you erase drive.
Or maybe other tools will work?

Windows wants either unallocated space or blank drive.
Following below 2 documents I succeeded partitioning the SSD drive running Windows Command Prompt
1)
How to Create a Partition or Volume in Windows using Command Prompt
[https://www.technohelper24.com/create-partition-windows-using-command-prompt/](https://www.technohelper24.com/create-partition-windows-using-command-prompt/)

2)
Get No Volume Selected Error While Formatting Partition [Solved] [Partition Manager]
[https://www.partitionwizard.com/partitionmanager/there-is-no-volume-selected.html](https://www.partitionwizard.com/partitionmanager/there-is-no-volume-selected.html)

But still unable to install Windows10 Home as reported previously, encountering the same problem.

DISKPART> list volume```

Volume 0 DVD-ROM
Volume 1 NTFS Partition 68 GB Healthy
Volume 2 FAT32 Removable 3828 MB Healthy

```

Regards

---

### Post by oldfred on 2020-10-18
Are you using a 4GB flash drive for Windows?
Windows .wim file is now over 4GB, so Windows needs 8GB flash drive as minimum.
And you have to split .wim file to have it fit in FAT32 formatted partition as 4GB is max for FAT32.

---

### Post by satimis on 2020-10-18
> **oldfred said:**
> Are you using a 4GB flash drive for Windows?
Windows .wim file is now over 4GB, so Windows needs 8GB flash drive as minimum.
Yes, OK I'll burn a new USB boot stick with size >8GB, or using a SanDisk card

> 
And you have to split .wim file to have it fit in FAT32 formatted partition as 4GB is max for FAT32.
Could you please explain in more detail.  Thanks

---

### Post by oldfred on 2020-10-18
Use the Windows installer tool as that splits the .wim file.
Most instructions on Internet for for older verisons of Windows where .wim file was less than 4GB and fit on FAT32 formatted partition.
And to boot in UEFI mode, .efi boot files have to be on FAT32 formatted partition for UEFI to read it.

For Windows ISO with .wim > 4GB
[https://ubuntuforums.org/showthread.php?t=2444665](https://ubuntuforums.org/showthread.php?t=2444665)
[https://github.com/ValdikSS/windows2usb](https://github.com/ValdikSS/windows2usb)

Someone posted this, but I do not know.
Latest Windows made .wim file smaller so extraction works again, depending on version.
UEFI only uses FAT32 which has a size limit on one file of 4GB, but Windows wim is now too large, extracted into a NTFS partition and only boot files in FAT32.
[https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/](https://techbit.ca/2019/02/creating-a-bootable-windows-10-uefi-usb-drive-using-linux/)
[https://itsfoss.com/bootable-windows-usb-linux/](https://itsfoss.com/bootable-windows-usb-linux/)
[https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files](https://help.ubuntu.com/community/Installation/iso2usb/diy/windows-installer-for-big-files)

---

### Post by satimis on 2020-10-26
> **oldfred said:**
> Use the Windows installer tool as that splits the .wim file.
Most instructions on Internet for for older verisons of Windows where .wim file was less than 4GB and fit on FAT32 formatted partition.
And to boot in UEFI mode, .efi boot files have to be on FAT32 formatted partition for UEFI to read it.
....... 
Hi oldfred,

Thanks for your advice and links.

Through heavy searching on Internet, I found that it can install Win10 Home direct on its ISO without CD or DVD or USB installer.

Performed following test.

1) Disconnected all hard drives on the spare PC except the 120G SSD old hard drive (drive sda) for installing Windows10 Home.

2) Start pc with Ubuntu 20.04 startup USB boot disk, running Ubuntu 20.04 desktop without installing it. 

3) Plugin a SanDisk 64G disk, mounted on an USB adapter (drive sdc)

4) Ran fdisk to partition and format the drives
$ lsblk```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sdb      8:16   1    15G  0 disk /cdrom
&#9500;&#9472;sdb2   8:18   1   2.4M  0 part
&#9492;&#9472;sdb1   8:17   1   1.6G  0 part
sr0     11:0    1  1024M  0 rom  
loop0    7:0    0   1.5G  1 loop /rofs
sdc      8:32   1  59.5G  0 disk
&#9500;&#9472;sdc2   8:34   1   4.5G  0 part /media/ubuntu/FE8B-90DA
&#9492;&#9472;sdc1   8:33   1    55G  0 part /media/ubuntu/FDE7-48BF
sda      8:0    0 119.2G  0 disk
&#9500;&#9472;sda2   8:2    0  19.2G  0 part
&#9492;&#9472;sda1   8:1    0   100G  0 part /media/ubuntu/41DA529D73772987

```

5) Remove drive sdc.  Plugin it on the daily working PC and copied windows10 Home ISO on it (sdc1 partition).

6) Plugin drive sdc on the spare PC again
$ ls -al /media/ubuntu/FDE7-48BF```

total 3429540
drwxrwxrwx 1 ubuntu ubuntu       4096 Oct 25 21:23 .
drwx------ 5 ubuntu root          100 Oct 25 21:23 ..
-rwxrwxrwx 1 ubuntu ubuntu FDE7-48BF Oct 25 15:15 W10.HOME.X64.en-US.Apr2016.iso

```

7) Start/Open sdc1 on File Manager
Double click Windows 10 Home ISO to extract it.

$ ls -al /media/ubuntu/FDE7-48BF
-> Start Windows 10 Home folder```

boot (folder)
efi (folder)
sources (folder)
support (folder)
autorun.inf
bootmgr
bootmgr.efi
setup.exe

```

But I couldn't run setup.exe without wine.  I was not allowed to install wine on Ubuntu 20.04 desktop which was NOT installed but under "Try"

Any advice?  Thanks

Regards

---

### Post by oldfred on 2020-10-26
You cannot run setup.exe from Linux. You have to boot into installer from UEFI (or BIOS). And mode you boot UEFI or BIOS is then how it installs.

If .wim file in Souces is less then 4GB you can extract directly to a  FAT32 formatted partition with boot/esp flags on flash drive. That will only boot in UEFI mode as /EFI/Boot/bootx64.efi exists for UEFI boot.

I have the 1909 version and the install.wim is 4.3GB or too large.

---

### Post by satimis on 2020-10-26
> **oldfred said:**
> You cannot run setup.exe from Linux. You have to boot into installer from UEFI (or BIOS). And mode you boot UEFI or BIOS is then how it installs.

If .wim file in Souces is less then 4GB you can extract directly to a  FAT32 formatted partition with boot/esp flags on flash drive. That will only boot in UEFI mode as /EFI/Boot/bootx64.efi exists for UEFI boot.

I have the 1909 version and the install.wim is 4.3GB or too large.
Hi oldfred,

I can start Windows 10 setup on BIOS -> UEFI boot, but it always popup an warning```

Windows cannot open the reqired file C:\Sources\install.esd. .......
```
install.esd is in Sources folder.  Neither I can find a way converting install.esd to install.wim on Ubuntu 20.04 desktop.

Advice would be appreciated.  Thanks

Regards

---

### Post by oldfred on 2020-10-26
This was in the link above. No idea if it works. He uses NTFS partition for Sources.
[https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/](https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/)

---

### Post by satimis on 2020-10-31
> **oldfred said:**
> This was in the link above. No idea if it works. He uses NTFS partition for Sources.
[https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/](https://win10.guru/usb-install-media-with-larger-than-4gb-wim-file/)
Hi oldfred,

Problem "no device driver found ..... etc."

There is NOT THING WRONG on burning Win10 USB boot disk.  Following articles solve the problem.  In my case I just change the USB port for plugin the Win10 boot USB disk.

[2 Fixes] USB Windows 10 Clean Install - A Media Driver Your Computer Needs is Missing
[https://www.youtube.com/watch?v=xNIdOs_50r4](https://www.youtube.com/watch?v=xNIdOs_50r4)

Fix- No device drivers were Found Windows installation problems
[https://thegeekpage.com/no-device-drivers-were-found-windows-installation/](https://thegeekpage.com/no-device-drivers-were-found-windows-installation/)

A media driver your computer needs is missing windows 10 install FIX
[https://www.youtube.com/watch?v=2G3hJdx89D8](https://www.youtube.com/watch?v=2G3hJdx89D8)

Now my attempt to install Win10 on physical disk and dual boot Windows/Linux system comes to an end. 

The story to install Win10 on physical disk began from purchasing a new Dell 32" 4K display, U3219Q IPS display, at end of September, last month.  The display flickers NOW and THEN.  I have tried to fix the problem myself without result, sometime good and another bad.  It can't be predicted when the problem will come nor to reproduce the problem.

Finally I contacted Dell Technical Support.  Dell requested me to test the display on a Windows PC, with Windows installed on a physical hard drive.  I told them that I can't satisfy their request because all Windows here are running on VMs of Oracle VirtualBox.  Finally Dell advised me testing the display on its built-in self-testing system as follow;

1. Turn on the PC
2. After the PC is running, disconnect the cable connected the display to PC, in my case HDMI cable.
3. The screen will turn to dark green.
4. Pressing the 1st screen button, next to the power button about 5 seconds, the screen will turn to a red screen
5. and again, then becomes yellow screen etc.

I told Dell that after pulling out the HDMI cable at back of the PC, the screen turning to a black/dark screen while the power light still on, white light.  Then Dell told me stop testing further because unfortunately I have a defective display and they will replace it.  Yesterday the forwarder of Dell confirmed me by phone that the replacement will be effected on next Monday afternoon.

My installation of Win10 on physical disk and dual boot will come to a conclusion.  All Windows here are running on VMs, for testing purpose only NOT for production.  

I stopped installing Windows on bare metal, physical disk, more than 20 years ago ever since stepping away from Windows turning to BSD -> then Unix -> now Linux.  The best Linux OS is Linux from scratch, in my opinion.

Linux from Scratch
[http://www.linuxfromscratch.org/](http://www.linuxfromscratch.org/)

I tried it before about 15 years ago.  It took 5 days and nights continuously to complete its building on a single core CPU PC.  After finishing building only Text Editor was running.  Then I have to continue install, browsers, office, other packages etc.  It is a very rigid Linux OS, not easily hacked.  Hackers are not easy to know how you build and configure the core around the kernel.  Nowadays on 8-core CPU PC I suppose the time of its building will be shorten dramatically

Anyway, lot of thanks for your assistance and time spent.

Regards

---

### Post by helen314 on 2020-10-31
I had same experience with Linux years ago. No need to refresh that bad memory.
The only "reason" I switched to Linux was financial and there is no need to discuss how  
"hackers friendly" 'and not user friendly Linux was then and still is today. 

I have been in similar situation recently.
I no longer run Windows , just WINE when  there is no choice of Linux version of the application.


It seem that majority of Windows / Ubuntu mutiboot system installation gets sidetracked in 
resolving BIOS and UEFI "differences". 

I simply do not get why it is such issue  - if there are options of getting OS ISO  which will boot using either boot method.
Maybe I am looking at it with KISS attitude - but when installing OS using ISO  why does it matter how  the ISO itself gets booted?
Your hardware / firmware  "setup" should care of that. 

My copy of Ubuntu IOS boots either way and I have a choice , with clean "OS destination hardware " to select BIOS or UEFI boot 
method for the installation of the actual OS boot. 

It cannot get much simpler IMHO. 

Again , I do not do Windows, but why it would not work same in  installing Windows?

I have applied this process - make sure there is a unallocated  space on destination harware - min 8GB.
Run  ISO boot setup  in " try it , do not install"  mode.

After it boots just run install. 
After the install and reboot - make sure there is yet another unallocated disk space and "rinse and repeat" another ISO install.

This time  install alongside existing  OS and again follow instructions .
After another reboot you have dual boot  - both Ubuntu , for simplicity - system.

This should work same , choosing second ( or third) OS as Windows.

---

### Post by satimis on 2020-10-31
> **helen314 said:**
> I had same experience with Linux years ago. No need to refresh that bad memory.
The only "reason" I switched to Linux was financial and there is no need to discuss how  
"hackers friendly" 'and not user friendly Linux was then and still is today. 

I have been in similar situation recently.
I no longer run Windows , just WINE when  there is no choice of Linux version of the application.
.......

Hi helen314,

Thanks for your advice.

I stopped running multi-boot system for years running virtualization instead.  I have 3 PCs all running Oracle VirtualBox with Ubuntu 20.04 desktop as host.  It needs not caring the booting system.  Should I need to test a new OS I just install it on VM.

V2P cloning a VM on a physical drive is NOT complicate.  Unfortunately Windows doesn't work on this technology.  I have no idea on MAC and never run it before.

I still keep Windows but running them on VMs and for testing only.

Edit
==
Virtualization is ideal for sharing hardware
Container "Docker" is deal for sharing software
Try them.
Container needs to run on VM

Regards

---

