---
title: "Dual booting with 4 physical drives (win7/Kubuntu)"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by brado2 on 2016-01-14
I have two SSDs (256 and 128GB) and two HDDs (1 and 2TB). I have been trying to install Kubuntu 14.04 alongside windows7, each on their own SSD (128 for kubuntu, 256 for Win7 and have each other drive be NTFS storage both OS's can see), but have either ended up with one or the other, no matter which drive I select in BIOS. sometimes I just get a grub error. I tried using boot-repair, which seemed to detect my windows install (grub only showed Ubuntu) and even after the install, grub still shows only Ubuntu...

I did manage to save my paste from boot-repair though

[http://paste.ubuntu.com/14501134/](http://paste.ubuntu.com/14501134/)

Any help on this would be greatly appreciated.

Motherboard: gigabyte ga-z97x-gaming 3
RAM: 4GB ddr3
CPU: i5 4690k
GPU: amd HD 7850 x2
HDD: WD Black 1tb and WD black 2tb
SSD: Samsung 256 and OCZ 128

---

### Post by brado2 on 2016-01-14
Might be related, the two physical HDDs and 256GB SSD no longer show up when I issue df -h (ever since boot-repair)

---

### Post by oldfred on 2016-01-15
You have a new high performance UEFI system, but installed Windows in the 35 year old BIOS/MBR configuration.
You then did install Ubuntu in the UEFI boot mode with gpt partitioning and full drive LVM/encryption. Do you want/need encryption? That makes it a lot more complicated to maintain. LVM is for advanced users. 

UEFI and BIOS are not compatible. You can then dual boot from UEFI boot menu, not grub. Once system starts in one mode it cannot switch.

Boot-Repair's auto fix did you no favors as it just reinstalled a BIOS boot grub to the MBR of every drive. With multiple drives, you always want Boot-Repair in advanced mode and choose one operating system and one (same drive as install) drive to repair boot loader. You also want to repair system in mode installed. You can boot Ubuntu/Boot-Repair in either UEFI or BIOS boot mode.

You can also boot Ubuntu from a gpt partitioned drive with either BIOS or UEFI. With BIOS you have to have a 1 or 2MB unformatted partition with the bios_grub flag. With UEFI you have to have the ESP - efi system partition FAT32 formatted with boot flag. I normally create partitions in advance and have added both. Old BIOS system then used bios_grub. And drive was compatible with my new UEFI system. Since I stopped Windows XP in 2011, I have only partitioned drives with gpt, including most flash drives.

Short term, only since you have Windows in BIOS mode, it may be better to have Ubuntu in BIOS boot mode. But long term you may want to use UEFI and gpt partitioning. Windows only boots in BIOS mode from MBR and only in UEFI mode from gpt, so drive partitioning is important.

Use Boot-Repair's advanced mode to install a Windows boot loader to sdc. Or use your Windows repairCD/flash drive to run fixMBR. Then from UEFI/BIOS boot menu you can directly boot Windows.

You can add a bios_grub partition to sdd. Shrink ESP by a few MB and create the 1MB unformatted bios_grub partition and reinstall grub only to sdd in BIOS boot mode with Boot-Repair.

How you boot install media, both Windows & Ubuntu is then how it installs, either UEFI or BIOS.

       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by brado2 on 2016-01-15
Here are two screenshots from the boot-repair screen. I'm a little confused by the procedure, as there looks like there is more than one way to:
> Use Boot-Repair's advanced mode to install a Windows boot loader to sdc.  Or use your Windows repairCD/flash drive to run fixMBR. Then from  UEFI/BIOS boot menu you can directly boot Windows.

Boot-repair has an option for "restore MBR" in the second screenshot. The first screenshot shows what looks like the first option you mentioned in the quote, however, why is sda listed? Do I need to somehow remove that since Windows is only installed on sdc? sda is my 2TB drive, (also curious why sdb and sdd are not listed on the left during 'df -h', but that's another matter). 

Also, why is GRUB greyed out? I believe your steps called for using it. Does this mean that the installation media booted in UEFI, therefore Grub is not needed?

Sorry I'm asking so many tangent-y questions. I'm new and want to get a grasp on this so that I have a better understanding of what's going on under the hood.

---

### Post by oldfred on 2016-01-15
Please attach screen shots. Not everyone has high speed Internet and it may cause issues.
You can easily attach with paper clip icon in forum's advanced editor.

Not sure now what order Boot-Repair is seeing drives. Did you change SATA ports?

System default to installing boot loaders to sda. Most BIOS are set to default to boot from sda. And UEFI install of grub, no matter what you say will only install to sda's ESP. That may be another issue for your system.

With Windows when installing it uses the drive set as default boot for its 100MB boot partition & boot loader in the MBR. Often best then just to have the drive with Windows as first, usually SATA port 0, then from Linux it will be sda.
But for grub to install initially correctly you will need an ESP on drive seen as sda. I have tried installing a second Ubuntu to sdb or sdc as flash drive and it always overwrites my primary UEFI boot /EFI/ubuntu on sda. I have learned to back up my ESP. :) But I do then copy /efi/ubuntu from ESP on sda to ESP on sdb. System only uses sda to boot, but since all my installs on my UEFI system are UEFI, I can use grub to choose what to boot. Extra ESP on sdb is just incase sda drive fails, so I have a boot loader on second drive also.

If you want to be absolutely sure you can disconnect all drives, but Windows drive. But installing boot loader to incorrect drive as long as it is MBR, will not matter. It just may not boot Windows if not on Windows drive.

---

### Post by brado2 on 2016-01-15
I'm using the same ports as before. I just opened my case, my ports are as follows:

SATA0: WD 2TB
SATA1: WD 1TB
SATA2: SSD 256GB
SATA3: DVD
SATA4: SSD 128GB
SATA5: Empty

which makes sense with the two drives I saw with df -h
```

/dev/sda1       1.9T  1.2T  697G  63% /mnt/boot-sav/sda1
/dev/sdc1       233G   15G  219G   7% /mnt/boot-sav/sdc1

```

I'm a little confused by your post, so allow me to clarify:

I decided to take the route of using BIOS over UEFI for two reasons:

1: My BIOS options screen has an option to boot devices with BIOS/UEFI, or both. When I select UEFI, it says that I do not have a boot drive (even with the windows 7 install disc in, and that selected as the default boot device)

2: When I attempt with "both" option and go to the W7 partitioning screen, I cannot make it match what the "[SIZE=2]How to Install Windows 7 Using the "Unified Extensible Firmware Interface" (UEFI)" article on sevenforums has (screenshot of what they have attached)

Therefore, I believe it'll just be easier in the short term to just use BIOS.



With that said, do your instructions in your latest post assume a BIOS setup? I can move which ports connect to which SATA devices. With that said, which ports would you recommend I use for which devices to optimally configure this dual boot setup? Both the windows7 and Ubuntu will be fresh installs. All of my backed up data is on the 2TB WD (currently SATA0/sda)
[/SIZE]

---

### Post by brado2 on 2016-01-15
I just restored the MBR with boot-repair (snapshot1.jpg or the 2nd picture of Post #4) of the first drive with the boot partition being sdc and this is what I have now:

[http://paste.ubuntu.com/14511826/](http://paste.ubuntu.com/14511826/)


Given this:

```

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Windows 7/8/2012 is installed in the MBR of /dev/sdb.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdc.
 => No boot loader is installed in the MBR of /dev/sdd.


```
Did I do this step correctly, and if not, what should these drives look like in this type of logging?

If I want to install Ubuntu to sdd, have windows7 on sdc, and decide on my OS at boot time using Grub, do I manually partition? If so, what options (see attached)? I don't see any option in the installation that specifies UEFI vs BIOS in either option.


Also, are these types of issues present in 15.04? If not, I can simply burn another DVD with that distribution and be on my way :)

---

### Post by oldfred on 2016-01-15
15.04 will expire in just a couple of weeks. Use 15.10, 16.04 will be out in April and will be a LTS version.
       [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)
    
I typically install the LTS version as main working install and on other drives have test installs of each of the newer versions.

With BIOS installs you want to use Something Else and be sure to choose the same drive as you install Ubuntu into as choice for grub2's boot loader.
I like to use gpt for Ubuntu only or data drives and include both an ESP & bios_grub. Then later you do not have to make major changes to convert to UEFI if desired. I use gparted to partition in advance and have to first change from default of MBR(msdos) to gpt(GUID).

Even if you partition in advance, you still need to use Something Else to choose where grub installs. And then set BIOS to default boot to that drive. Keep Windows boot loader in the Windows drive as grub really only boots working Windows. So when Windows breaks you can still directly boot and maybe use f8 to get into repair console. Grub boots into Windows too quick for you to have time to press f8.

       Oldfred's current partitions Dec 2015
[http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](http://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

    On my old BIOS system I used gpt, and had separate data partitions. Until stopping XP I has a shared NTFS data partition for a lot of data for either system like Firefox & Thunderbird profiles & photos for Picasa. Now only data partition is Linux but shared among several Ubuntu installs.

Windows 7 default install is BIOS only, you have to copy to flash drive and move Windows boot file to /EFI/Boot/bootx64.efi to be an external device UEFI boot.
        How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)

For both Windows & Linux, how you boot install media UEFI or BIOS is then how it installs. You cannot start process and change. Although if using gpt, Boot-Repair can convert a BIOS install of Ubuntu to UEFI or vice-versa if you have correct partitions. Boot-Repair will not auto add partitions.

---

