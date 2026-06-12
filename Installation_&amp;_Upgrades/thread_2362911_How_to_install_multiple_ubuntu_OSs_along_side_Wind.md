---
title: "How to install multiple ubuntu OSs along side Windows 10"
date: 2017-06-03
forum: Installation &amp; Upgrades
---

### Post by Ralph L on 2017-06-03
I recently bought an Acer Aspire E5-575G-57D4 laptop and and want to install several different Ubuntu type operating systems along side Windows 10 on it.  I have been following the instructions in [https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295), but came to the point, under Partitioning, where it says that I can have only one ubuntu partition, if I use UEFI (or at least that's how I interpret it).  I have successfully shrunk my Windows 10 partition to about 24 GB, so I now have space to hold several different ubuntu partitions, but how do I format the unformatted part of the disk so that Windows will continue to run and I have several partitions for various versions of ubuntu, plus a data partition?

Any help appreciated...

And I know I shouldn't ask Windows questions here, but if anybody knows, how do I boot from a Windows 10 USB Recovery Drive that I created?  The UEFI/BIOS firmware doesn't even see my USB Recovery Drive, although it will boot fine from a Xubuntu 17.04 Live Flash Drive.

---

### Post by oldfred on 2017-06-03
I think oldfred's thread says only one ESP per device/drive. 
But with Ubuntu, all installs use same /EFI/ubuntu for grub. And last install is then one in control. Or you have to backup and manage which install you want as default boot by changing /EFI/ubuntu/grub.cfg. I quickly learned with first second install to backup ESP.

I have two Ubuntu installs on my Dell which has Windows 10 all in UEFI mode.
But my main working desktop has two Ubuntu on SSD, and several more on HDD.

Do not make Windows 10 partition too small. It likes 30% free to work well. On Dell I made it 50GB as Windows 8 and never planned to use Windows. But then had to use Windows to watch Comcast/Xfinity and updated to Windows 10. But also changed to 100GB to have room.

If Windows is not booting in UEFI mode, is /EFI/Boot/bootx64.efi there? All external devices boot from that file for UEFI. And it probably will not boot in BIOS mode.
       If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode 
            Windows bootable USB from Ubuntu BIOS or UEFI, uses grub for BIOS boot.
[http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html](http://onetransistor.blogspot.ch/2014/09/make-bootable-windows-usb-from-ubuntu.html) 
    
I create multiple 25GB / (root) partitions and a larger /mnt/data partition with gparted. Then use Something Else to install. 
Once with my old system I had many partitions on a new large sdc drive. And installed Ubuntu to wrong partition, the data partition. Luckily I had not yet copied data so not big issue, but learned to keep track as installer only shows previous installs, not labels which I normally add.

       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

---

### Post by Dennis N on 2017-06-03
> how do I format the unformatted part of the disk so that Windows will continue to run and I have several partitions for various versions of ubuntu, plus a data partition?

If you have uallocated space, you define the size of the partitions and format them to fit their intended use. When you make partitions for Linux, you use Linux partitioning tools to do that - most people use gparted - and you can make them while booted to your live install media before starting the installer. gparted is installed on the live media for your use in doing that. You can also make them after starting the installer when you use the "Something Else" install option and reach the screen showing the disk partitions. In any case, when specifying your partitions, you use the "Something Else" option when installing.

Ubuntu installed in UEFI needs a root partition and an EFI system partition. Ubuntu used to require a swap partition, but now you can forget about that as newest Ubuntu release (17.04) uses a swap file if there is no swap partition.

The EFI system partition Windows uses will also be used by Ubuntu, so you don't need to make another one. 

I recommend UEFI for all installs when possible.

My current partition scheme over two internal drives. "Common-Files" is my shared data partition.

```
Model: ATA WDC WD5000AAKX-0 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI-System-Partition  boot, esp
 2      538MB   42.5GB  41.9GB  ext4            Xubuntu-1404
 3      42.5GB  46.7GB  4194MB  linux-swap(v1)
 4      46.7GB  177GB   130GB   ext4            Common-Files
 5      177GB   206GB   29.4GB  ext4            Xubuntu-1604
 6      206GB   233GB   27.3GB  ext4            Lubuntu-1704


Model: ATA WDC WD10EZEX-22B (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  211MB   210MB   fat32           EFI System Partition  boot, esp
 2      211MB   33.8GB  33.6GB  ext4            Ubuntu-MATE-1410
 3      33.8GB  38.0GB  4194MB  linux-swap(v1)
 4      38.0GB  58.9GB  21.0GB  ext4            Mint-18-XFCE
 5      58.9GB  86.2GB  27.3GB  ext4            Ubuntu-MATE-1404
 6      86.2GB  113GB   27.3GB  ext4            Xubuntu-1504
 7      113GB   141GB   27.3GB  ext4            Lubuntu-1404
 8      141GB   168GB   27.3GB  ext4            Mint-17-MATE
 9      168GB   195GB   27.3GB  ext4            Manjaro-XFCE
10      195GB   195GB   83.9MB  fat32           EFI System Partition  boot, esp
11      195GB   223GB   27.3GB  ext4            Korora-23-XFCE
12      223GB   250GB   27.3GB  ext4            Mint-17-XFCE
13      250GB   277GB   27.3GB  ext4            Korora-25-Gnome
14      277GB   277GB   83.9MB  fat16           EFI System Partition  boot, esp
15      277GB   315GB   37.7GB  ext4            Ubuntu-Gnome

```

---

### Post by Ralph L on 2017-06-03
Thank you Old Fred and Dennis N for replying.  I really appreciate it.
1.  Dennis:  You indirectly answered my question about why the Windows 10 Recovery Drive (that I made because I am concerned that I may blow Windows in installing Linux).  Your example showed that the esp flag was set on your uefi partition.  Windows Recovery Creator did not set that flag, so I set it using gparted.  Doing that allowed the Recovery Drive to boot.  THANK YOU.  I've been stalled on that one, searching google, for 2 days.  However, I discovered that when gparted set the esp flag, it cleared the lba (logical block addressing) flag.  Is that a problem???  The Recovery Drive seems to run ok with lba cleared.
2.  I Live booted a flash drive with xubuntu 17.04 on my new computer.  The reason I chose 17.04 rather than 16.04 LTS is that I read a web site that said older versions of ubuntu were not managing power correctly on newer computers with ssd (I have 256 GB of ssd) and that my Acer promised 12 hour battery life would be reduced to about 4 hours with 16.04.  Do you know anything about that????  Moreover, the web site said that I needed Linux Kernel 4.11 to get the fix and even 17.04 has only Kernel 4.10.0-19.  Do you know if the fix has been backported into xubuntu 17.04, or better yet xubuntu 16.04LTS???  This is the web site that discusses the problem: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1664602) .
3.  I started using gparted to create new partitions for xubuntu on my new computer's ssd.  However, I get a message that says "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes."  What is gparted trying to tell me??  I went ahead and formatted several partitions, but it keeps giving that message.  I am concerned that the new ssd has a larger block size and that if I let gparted use the smaller (512) block, the ssd will run slower, or maybe only store 512 bytes in a 2048 block.  I don't really understand all the nuances of different sized logical blocks, physical blocks, sector size and disk allocation units.
4,  I installed xubuntu 17.04 on my new computer, but I can't boot to xubuntu. I am never given a choice.  Are there flags that I need to set to get uefi firmware to look at the xubuntu disk partition??  Do I need to install something (perhaps grub) in the uefi partition??  Do I need to set something in the uefi firmware using F2???  Note:  I have disabled Secure Boot in uefi firmware.

Any further help appreciated....

---

### Post by oldfred on 2017-06-03
Is this really shown on the flash drive you are using. I have seen it there.
> The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes
What does this show?
 sudo gdisk -l /dev/sda 
And is start divisible by 8 for every partition?


 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)

Do not know about kernels.
Have seen users use ppa to add newer kernel, but then you are on your own more as a developer/tester.

---

### Post by Dennis N on 2017-06-03
Glad to hear my little post helped in some way. I really don't know about the lba flag.

Zesty (17.04) latest kernel update was to 4.10.0-21. If I read correctly the bug page says fix released for Zesty.

>  I started using gparted to create new partitions for xubuntu on my new computer's ssd. However, I get a message that says "The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes."

I see this message if gparted scans my install media made with Imagewriter. But no effect on the resulting OS installation. Just click on Ignore.

> I installed xubuntu 17.04 on my new computer, but I can't boot to xubuntu. I am never given a choice. Are there flags that I need to set to get uefi firmware to look at the xubuntu disk partition?? Do I need to install something (perhaps grub) in the uefi partition?? Do I need to set something in the uefi firmware using F2??? Note: I have disabled Secure Boot in uefi firmware.

I'm no expert on technical details, but Ubuntu installer should as part of the install job automatically install (some) boot files to the EFI system partition and create an entry in the UEFI boot menu in the default (1st position) to point to those files. Did you try the one-time boot menu to see if Ubuntu is on it? If necessary, make a new question on this "boots straight to Windows" problem in this Installation forum and one of the guys who knows more than I do about working with Windows dual boot can help. I haven't used Windows since 2007 and XP.

You can install Ubuntu with or without secure boot enabled. Originally, I had it enabled, then had to change when I found some non-Ubuntu distros like Linux Mint will not install with secure boot on.

---

### Post by Ralph L on 2017-06-03
Guys:  Thanks again for the responses!!
1.  Here is the output of running gdisk:```
xubuntu@xubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 500118192 sectors, 238.5 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 993C3DA3-B65C-4727-877A-FF0234D3C547
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 500118158
Partitions will be aligned on 2048-sector boundaries
Total free space is 34837101 sectors (16.6 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          239615   16.0 MiB    0C01  Microsoft reserved ...
   3          239616        51107839   24.3 GiB    0700  Basic data partition
   4       498020352       500117503   1024.0 MiB  2700  Basic data partition
   5       476542976       498020351   10.2 GiB    8300  Xubuntu 17.04
   6       455065600       476542975   10.2 GiB    8300  
   7       433588224       455065599   10.2 GiB    8300  
   8       412110848       433588223   10.2 GiB    8300  
   9       390633472       412110847   10.2 GiB    8300  
  10       373649408       390633471   8.1 GiB     8200  
  11        85942272       373649407   137.2 GiB   8300  Shared Data
xubuntu@xubuntu:~$ 

```The beginning sectors of all the partitions are divisible by 8, so I guess that means that its properly formatted and will run at speeds up to its potential.
2.  Now my problem is getting it to boot to xubuntu.  It just goes straight to windows never giving me a choiceu.  Dennis, I don't know how to examine the uefi partition.  Thunar doesn't mount it and doesn't display it.  The only place I see it is in gparted.  So I don't know how to check if there is a xubuntu file in the uefi partition.  Any suggestions????

---

### Post by yancek on 2017-06-03
Your gdisk output shows your EFI partition is the first partition on the disk so create a mount point and mount with commands below from a terminal:

```
sudo mkdir /mnt/sda1
```
```
sudo mount /dev/sda1 /mnt/sda1
```

You can then access the partition from a terminal by changing diretories:  cd /mnt/sda1
Or you can run the command:  ls /mnt/sda1
Or you can access it in Thunar at that location; /mnt/sda1

---

### Post by Dennis N on 2017-06-03
Did you try the one-time boot menu to see if the new Xubuntu is on it? It's the same menu you use to boot the live USB.

---

### Post by Ralph L on 2017-06-03
Thanks again for all the responses!!
I think I got it!!! This site explained the peculiarities of Acer systems:  [https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003) . Here were the tricky parts of buying an Acer:```
This probably also applies to other Acer models using InsydeH2O BIOS. After much messing around, this is how I got dual boot working on my Acer Aspire R14-471T:

1) Update to the latest BIOS (I know, it's UEFI, but I'm going to call it a BIOS). My new laptop shipped with 1.07, 1.10 is the latest as of this posting.
2) Shut down, then while starting back up hit the F2 button many times until the BIOS Setup Utility loads.
3) In the "Main" menu, set the "F12 Boot Menu" option to "Enabled". Press F10 to Save and Exit, then once Windows loads shut down again.
4) Insert your USB flash drive with your 64-bit Ubuntu installer on it.
5) Power on and keep pressing F12 until the boot menu pops up. Select the flash drive, boot, and install Ubuntu.

This is where things get tricky:
6) After ubuntu reboots, it will boot back into Windows. Shut down again. Reboot and hit F2 to enter the BIOS again.
7) Under "Security", choose "Set Supervisor Password", and set one. You will need this password any time you go back into the BIOS. A bunch of options 
on the page should change from grey to blue.
8) The "Select an UEFI file as trusted for executing" should now be available. If it's not available, check that Secure Boot is still Enabled, if not, Enable it. Select 
it, and navigate to HDD0->EFI->ubuntu->grubx64.efi. The BIOS will ask you for a name for it, I called it Grub.
9) Hit F10 to save and exit, then immediately hit F2 again to re-enter the BIOS. 
10) Now go to "Boot", set "Secure Boot" to "Disabled", and arrow down to the bottom of the list to your new "Grub" entry. Hit F6 until it's the top of the list.
11) Hit F10 one last time. Your system should now reboot to the Grub boot loader!
```Low and behold I got the usual ubunbtu boot menu.  I don't know if I will have to go through this again, when I install another version of Ubuntu, but I guess I will find out.....

Thanks again to everybody that helped me.  I would never have figured it out on my own.

---

### Post by oldfred on 2017-06-03
Did you set the UEFI supervisory password and enable trust. This is unique to most Acers.
And you need to have newest UEFI from Acer for your system.
Some older threads suggested downgrading UEFI as version did not have trust setting, but newer threads said newest UEFI was fixed.

       Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)


Ubuntu used to mount the ESP with defaults but changed to umask=0077so in effect hidden.
       14.04 fstab entry defaults
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 fstab entry umask=0077
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1 

I change mine to default like it used to be, but they may have changed to lock the efi as perhaps a virus could write into it if you were phishing to into using sudo to allow a virus to install something. FAT32 does not have ownership nor permissions, so mounting is the only control they have.

---

### Post by Dennis N on 2017-06-03
Congratulations! But, looking at your partitions 5 through 9, I think you are going to need more than 10.2 GB for your installs. I am already using more than that for root on Lubuntu 17.04, not counting my separate data partition. And I have not been running it that long.

---

### Post by oldfred on 2017-06-03
Agree with Dennis N.

My full install to flash drive is brand new and uses 4GB.
But my working install is 9.9GB with /home but all data in /mnt/data and some larger files in /home like .mozilla & .thunderbird profiles moved to data partition also. So /home is down to just a few user settings.

So I would at least make main working install 20 to 30GB. If just testing for a few days you may be able to get by with just 10GB. But have to watch that logs and files that grow over time do not fill / (root).

---

### Post by Ralph L on 2017-06-06
Thanks guys for the concern about OS partition size.  You may well be correct that I will have to increase a couple of them.  However, up to this point I have been able to get along with 10G partitions, even when installing a bunch of Kubuntu apps like kdenlive and digikam.  I have my firefox,thunderbird, pywo, libreoffice, templates, and wine profiles all on my data partition, so that helps.  But thanks for the warning!!!

---

