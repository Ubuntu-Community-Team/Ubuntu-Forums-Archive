---
title: "GRUB Installation Failed"
date: 2018-07-13
forum: Installation &amp; Upgrades
---

### Post by lawrence-joy on 2018-07-13
I previously downloaded Ubuntu 18.04 LTS .ISO file(s) to an USB flash drive. I clicked on the 2nd line that stated about installing, instead of the first line that says try it without installing. How it figured out that I have two SSDs, the one with Windows 10 and the other with Ubuntu 18.04 LTS, I don't know, but it said that 18.04 LTS was already loaded. It gave me a choice of doing a 2nd load, with the two installations being sided by side, or delete what was there and do a fresh install. I chose delete and install. It got about half way done with the install and I got "Grub installation failed". "The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot". "Installer crashed".

It asked if I wanted to do a bug report. I answered yes and it came up with information and I filled out my info. It accepted the bug report but I don't know where it went or where to go to look at it. Everything looked as it came from this Ubuntu forum as it asked for my e-mail and password and had my user name. There is no "bug report" tab here on the forum. Where did it go and how do I get to it to check status?

If I am running Ubuntu 18.04 LTS from my USB flash drive how do I get to the SSD with Ubuntu 18.04 LTS on it so I can issue the command at the terminal to wipe the SSD, that is set all the cells to zero. And then I would have the USB flash drive do an install. But how do I make sure the install goes to the SSD that is now blank?

---

### Post by oldfred on 2018-07-13
UEFI or BIOS?
What video card/chip?
If Windows 10 was pre-installed then it will be UEFI. If an upgrade from Windows 7 it probably is BIOS/MBR.
You need Ubuntu in same boot mode.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by jeremy31 on 2018-07-15
Post info while booted into the ISO on the flash drive for
```
lsblk; sudo blkid
```

---

### Post by lawrence-joy on 2018-07-16
To oldfred. At boot up to get to my SSD (Nr 2) I have to push the F11 key which gives me "Please select boot device:", which choices are:
SATA1: Samsung SSD 850 PRO 25
SATA4: Samsung SSD 850 PRO 25
UEFI: KingstonDataTraveler 2.0PMAP
What do you mean "UEFI OR BIOS?"
The video card is NVIDIA GEFORCE GTX, Mfg PN: ZT-71103-10L, Description: ZOTAC GeForce GT 730 - Graphic ZT-73G2128. This video driver is for my dual monitor system.

I put this PC together myself from parts and pieces ordered from Tiger Direct. The Windows 8.2 OS was not pre-installed. It came on a CD-ROM that I installed myself and as soon as I got a connection to the internet it upgraded to Windows 10. So was that BIOS or UEFI?
I had trouble trying to load Ubuntu 15.04 as the CD-ROM would not recognize that I had two SSDs. I eventually disconnected SATA1 (with Windows 10) and was able to do the load to SATA4. I then reconnected SATA1 and at the sign on I always have to interrupt with the F11 key so I can select SATA4, which has my Ubuntu OS.

How I got into this mess. I had been keeping up with the automatic announcements that there was a newer version. I would answer yes to everything and ended up with Kubuntu, besides a bunch of other software that I don't think I wanted or needed. A few months ago, maybe a half a year ago now, I answered yes to an upgrade notice and ended up with a message that said the upgrade failed. I was at Ubuntu version 17.10 when I tried to upgrade to 18.04 LTS from the Ubuntu website. It did not complete as there was a failure (again). I put a notice here on the Ubuntu forums about my problem and it was suggested to try the commands to repair and fix. That didn't work. The other suggestion was to download the .ISO image files to an USB flash drive, which I did. When I mount the USB flash drive, when in my Windows 10 OS, the directory/folder is listed as "uefi" with about a dozen files listed. I don't want Kubuntu and the other software that is loaded, so I have saved the few files and directories with files that I want to another USB flash drive. I then tried the install from the USB flash drive with the .ISO image files and got the GRUB failure as reported.

To jeremy31. I issued the command 'lsblk; sudo blkid' as you stated and got the following:
NAME   MAJ:MIN   RM   SIZE  RO   TYPE   MOUNTPOINT
loop0     7:0            0      1.7G   1      loop      /rofs
loop1     7:1            0     86.6M  1      loop      /snap/core/4486
loop2     7:2            0      140M  1      loop      /snap/gnome-3-26-1604/59
loop3     7:3            0      1.6M   1      loop      /snap/gnome-calculator/154
loop4     7:4            0     12.2M  1      loop      /snap/gnome-characters/69
loop5     7:5            0      21M    1      loop      /snap/gnome-logs/25
loop6     7:6            0      3.3M   1      loop      /snap/gnome-system-monitor/36
sda        8:0           0    238.5G  0      disk
-sda1     8:1           0     350M    0      part
-sda2     8:2           0    237.7G  0      part
-sda3     8:3           0    450M     0      part
sdb       8:16          0    238.5G  0      disk
-sdb1    8:17          0    222.5G   0     part
-sdb2    8:18          0       1K      0      part
-sdb5    8:21          0     16G      0      part    [SWAP]
sdc       8:32          1    7.3G      0      disk    /cdrom
-sdc1    8:33          1    1.8G      0      part
-sdc2    8:34          1    2.3M      0      part
sr0       11:0          1    1024M    0      rom
/dev/sda1: LABEL="System Reserved" UUID="FE046E3F046DFAD3" Type="ntfs" PARTUUID="e1386ff7-01"
/dev/sda2: UUID="E2C06F24C06EFDE3" TYPE="ntfs" PARTUUID="e1386ff7-02"
/dev/sda3: UUID="64CC6CB8CC6C85E0" TYPE="ntfs" PARTUUID="e1386ff7-03"
/dev/sdb1: UUID="b19bd4f5-e83c-4156-856b-368d6b82bd9f" TYPE="ext64" PARTUUID="117b202d-01"
/dev/loop0: TYPE="squashfs"
/dev/loop1: TYPE="squashfs"
/dev/loop2: TYPE="squashfs"
/dev/loop3: TYPE="squashfs"
/dev/loop4: TYPE="squashfs"
/dev/loop5: TYPE="squashfs"
/dev/loop6: TYPE="squashfs"
/dev/sdb5: UUID="33b15271-4efc-4d18-81f2-f703abcfa96f" TYPE="swap" PARTUUID="117b202d-05"
/dev/sdc1: UUID="2018-04-26-18-43-51-00" LABEL="Ubuntu 18.04 LTS amd64" TYPE="iso9660" PTUUID="2b192737" PTTYPE="dos" PARTUUID="2b192737-01"
/dev/sdc2: SEC_TYPE="msdos" UUID="044E-AC17" TYPE="vfat" PARTUUID="2b192737-02"

I hope this is enough information on my system and my problem to get an answer as to how to go about doing a clean install of 18.04 LTS to my SATA4 drive. I will take a look at the links given and see if I can figure out what they have to say.

---

### Post by oldfred on 2018-07-16
You must have newer UEFI hardware or you could not have booted an installer in UEFI mode which gives the 'grub-efi-amd64-signed' error as your actual installs all look like the 35 year old BIOS/MBR configuration.
Both Windows & Ubuntu install in the boot mode UEFI or BIOS, based on whether you boot installer in UEFI or BIOS boot mode. Your UEFI menu for booting flash drive with UEFI Secure Boot off will give two boot options, one UEFI:flash drive and other just "flash drive" where "flash drive" may be name, brand, or label of flash drive.

If a drive is only for Ubuntu I recommend using the newer gpt partitioning system that is normally used with UEFI. Ubuntu can boot in UEFI or BIOS from gpt. Windows only boots in BIOS mode form MBR and only in UEFI mode from gpt. If Ubuntu is on a gpt drive with both an ESP partition for UEFI boot and a bios_grub partition for BIOS boot, you later can easily reconfigure boot mode. Otherwise you have to backkup, erase drive,convert partitioning, repartition & reinstall.

Since Windows is BIOS, usually better to have Ubuntu in BIOS boot mode. If both are not in same boot mode, then you can only dual boot using UEFI boot menu, not grub. Grub only boots systems installed in same boot mode as Ubuntu/grub. And grub only boots working Windows.

Simple solution is to boot Ubuntu live installer in BIOS boot mode and reinstall.

If you want to know from about UEFI, see link in my signature below. At end is explanation of terms & links to more explanation of some of those terms if not familiar with UEFI.

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by lawrence-joy on 2018-07-17
To oldfred. I have read some of your links but need to read some more. Thank you for the enlightenment about I-O systems, the only thing I knew of was BIOS, never heard of UEFI until now.

I got into my Windows 10 (home version) OS, went to the system information, and found that my motherboard apparently has a BIOS system as the report is "BIOS Version/Date | American Megatrends Inc. V22.2, 2014-12-16". I got into the motherboard information and it had "BIOS Version E7693AMS V22.2 build date 12/16/2014". When I issue the command 'lsblk; sudo blkid' when on my USB flash drive with Ubuntu 18.04 LTS .iso image files, I see the listing and now understand that terms like UUID and PARTUUID are of the UEFI system.

Since I have separate drives for Windows 10 and Ubuntu I take it that I do not have a dual boot system, is this correct? Your statement "If Ubuntu is on a gpt drive with both an ESP partition for UEFI boot and  a bios_grub partition for BIOS boot, you later can easily reconfigure  boot mode". For a neophyte as I am anything dealing with Ubuntu is not easy. LOL. You have stated "If a drive is only for Ubuntu I recommend using the newer gpt partitioning system that is normally used with UEFI". It sounds like that is what I want to do. The question is, what are the explicit commands to use to accomplish erasing my SSD (I saw that the command is 'dd...something', but how do I make the command operate on my SSD number 2 when I am in the USB flash drive?), partitioning it with gpt, and installing Ubuntu 18.04 LTS from my USB flash drive?

I am grateful for all your teaching and insight in this matter.

---

### Post by yancek on 2018-07-17
> I see the listing and now understand that terms like UUID and PARTUUID are of the UEFI system.

They show and are used on both UEFI and Legacy/MBR systems, unrelated to whether  a machine is UEFI.

> Since I have separate drives for Windows 10 and Ubuntu I take it that I do not have a dual boot system, is this correct?

Dual boot isn't a specifically defined term but generally spearking, have two or more operating systems on the same machine would be referred to as dual booting.  As far as using GPT with a Legacy or UEFI system, I would suggest you read through the Ubuntu documentation at the link below and decide what you want. 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-07-17
Many vendors call their UEFI as BIOS since most users know that. But everything in last 5 years is UEFI as when Microsoft released Windows 8 about 5 years ago they required system to be installed in UEFI boot mode on gpt partitioned drive.

If you have nothing on Ubuntu drive, you can reinstall. But should have plans on backup for both Windows & Ubuntu as that is really required before any system change. We do make errors, and sometimes system does exactly what you tell it, not what you want. :)  

I have only used gpt for all new or totally reformatted drives since 2010.

I partition in advance and prefer to keep system separate from data. For newer users a separate partition for /home is easist way to do that, but still requires Something Else. I also prefer topartition with gparted in advance, but you can partition during install. Even if partitions created in advance, in Something else you  have to choose (change button) which partition is / (root) and which is /home, and formats & specify you want to use it. 

       It is recommended to use always GPT for UEFI boot as some UEFI firmwares do not allow UEFI-MBR boot. 
   For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap(prior to 17.10), but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]25-30+ GB Mountpoint / primary or logical beginning ext4
[*]all but 2 GB Mountpoint /home logical beginning ext4
[*]2 GB Mountpoint swap logical (not required with 17.04 and later uses a swap file, if no swap partition found)
[*]You do not need to create swap, as it either finds existing swap partition, or creates in fstab the following swapfile entry:
[/LIST]
   /swapfile                                 none            swap    sw              0       0 

You will not be able to fully install in UEFI mode, unless you disconnect other drive(s), so install drive seen as sda. UEFI install of grub with Ubuntu only installs to ESP on first drive, usually sda or NVMe first drive.
You can install in BIOS boot mode and later convert to UEFI if desired, if you have both bios_grub for BIOS and an ESP for UEFI. The only difference is the version of grub and some settings that automatically get changed when you install that version of grub. It has grub-pc for BIOS boot and grub-efi-amd64 for UEFI 64 bit installs.

---

### Post by lawrence-joy on 2018-07-19
oldfred: I finally got it to load! I won't bother you with the details but here is how the list now looks for the boot devices:
UEFI : Built-in EFI Shell
SATA5 : HL-DT-ST DVDRAM GH24NS
ubuntu (P3: Samsung SSD 850 PRO 256GB)
ubuntu (P3: Samsung SSD 850 PRO 256GB)
UEFI OS (P3: Samsung SSD 850 PRO 256GB)
SATA4 : Samsung SSD 850 PRO 25
SATA1 : Samsung SSD 850 PRO 25
Enter Setup

I don't know why there are three listings for Ubuntu, two that start with ubuntu and the one that starts UEFI OS. I can pick on any of the three and the system goes to my Ubuntu 18.04 LTS that resides on SATA4. If I pick on SATA4 or SATA1 listing, the system goes to my Windows 10 that resides on SATA1.

Thanks for all the help.

---

### Post by oldfred on 2018-07-19
Glad that worked.
Not exactly sure how Samsung's UEFI then works. But it works.
Ubuntu typically has two entries one shimx64.efi and one grubx64.efi. Shim is used for UEFI Secure Boot but works with secure boot off. The grub is for standard UEFI.

And often now a fallback or hard drive entry is also added which also boots something. Windows makes it a copy of their boot loader. Grub now installs it or Boot-Repair installs it. Its /EFI/Boot/bootx64.efi in your ESP - efi system partition partition.

---

