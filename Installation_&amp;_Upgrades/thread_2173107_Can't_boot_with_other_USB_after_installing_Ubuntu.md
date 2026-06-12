---
title: "Can't boot with other USB after installing Ubuntu"
date: 2013-09-08
forum: Installation &amp; Upgrades
---

### Post by fugue2 on 2013-09-08
Hi, I am new to Linux and Ubuntu. I just replaced the clumsy Win8 with Ubuntu on my new HP laptop. I erased everything and now I have only Ubuntu on my laptop. I decide to double (or triple) boot Win7 and Mint on my laptop. But now I find the USB live sticks for Win7 and Mint do not work on my laptop anymore. When I start up the laptop, it will jump directly into ubuntu (I changed the BIOS setting). Would someone please let me know how to boot the Win7 or Mint in a USB stick? (I searched online and find some words like "grub" but I have totally no idea what to do with that.)

The situiation i: I can [COLOR=#0000cd]only boot with the Ubuntu live USB stick, but the Win7 and Mint USB sticks that  used to work on my laptop does not work anymore[/COLOR].

Thanks for your time!!

---

### Post by sudodus on 2013-09-08
There is usually a hotkey, that you press during the very first part of the boot sequence, that allows you to select device to boot from.

It will be written on the screen for one or two seconds and can be Esc, F2, F9, F10, F12, Del, Enter (unusual) and probably also some other hotkey. Look for it and try!

Otherwise you must go into the BIOS menu and set the boot order to boot from the USB drive before the internal hard disk drive. It may work better if you have the USB drive plugged in when you enter the BIOS menu system, particularly if the USB drive is recognized as a hard disk drive (both are mass storage devices).

*Edit*: Or is it an issue with UEFI or not UEFI (CSM or 'old school BIOS')?

---

### Post by fugue2 on 2013-09-08
> **sudodus said:**
> There is usually a hotkey, that you press during the very first part of the boot sequence, that allows you to select device to boot from.

It will be written on the screen for one or two seconds and can be Esc, F2, F9, F10, F12, Del, Enter (unusual) and probably also some other hotkey. Look for it and try!

Otherwise you must go into the BIOS menu and set the boot order to boot from the USB drive before the internal hard disk drive. It may work better if you have the USB drive plugged in when you enter the BIOS menu system, particularly if the USB drive is recognized as a hard disk drive (both are mass storage devices).

*Edit*: Or is it an issue with UEFI or not UEFI (CSM or 'old school BIOS')?

Thanks for your reply. I don't think it is a BIOS issue. Sorry for not stating the issue clear enough. The problem is: I can only boot with Ubuntu USB stick, but other USB sticks that used to work on my laptop doesn't work anymore after I install Ubuntu.

---

### Post by sudodus on 2013-09-08
- If the other sticks need UEFI, and you have now set the computer for BIOS alias CSM, or vice versa, you will have problems. You need to sort this out. Then maybe you can use [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair").

- Have you checked that the other sticks really work in another computer?

- If the other sticks used to work in the same computer, I guess it is 'only a setting' in the BIOS menu system, because Ubuntu will not be started at boot time (it will make no difference). Now I'm talking about booting (starting to boot).

- Or are the other sticks booting, but then getting stuck somehow? I think they should boot independently of the harddrive, if it is there at all or what is stored in it.

---

### Post by oldfred on 2013-09-08
If system was Windows 8 then you had a gpt partitioned drive and UEFI booting.

If you totally reinstalled you may have BIOS or UEFI as Ubuntu boots with both. It also will boot from gpt drives with BIOS or UEFI. If reformated to MBR(msdos) then you can only boot with BIOS mode.

Windows only boots from gpt partitioned drives with UEFI, but Windows 7 is not UEFI by default but can be.
Not sure if Mint is UEFI or gpt aware.

You need to know if drive is gpt and if booting in UEFI or BIOS mode. All systems need to be in same boot mode.
Windows also has some specific partition requirements. It needs one partition before all data partitions also. And efi partition is supposed to be first per UEFI, but many Windows installs have efi near beginning of drive but not first.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

            Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
       Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> If system was Windows 8 then you had a gpt partitioned drive and UEFI booting.

If you totally reinstalled you may have BIOS or UEFI as Ubuntu boots with both. It also will boot from gpt drives with BIOS or UEFI. If reformated to MBR(msdos) then you can only boot with BIOS mode.

Windows only boots from gpt partitioned drives with UEFI, but Windows 7 is not UEFI by default but can be.
Not sure if Mint is UEFI or gpt aware.

You need to know if drive is gpt and if booting in UEFI or BIOS mode. All systems need to be in same boot mode.
Windows also has some specific partition requirements. It needs one partition before all data partitions also. And efi partition is supposed to be first per UEFI, but many Windows installs have efi near beginning of drive but not first.

       Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

            Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

    
       Convert Windows USB flash install to UEFI boot
[http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/](http://jake.io/b/2011/installing-windows-7-with-uefi-boot-on-an-x220-from-usb/)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


Thank you all for your replies. I seems I have a lot more to learn. I have no idea what gpt, UEFI are yet. My laptop was preinstallled with Win8 and I replaced it with Ubuntu but now I cannot install Win7 anymore.

Update:  I just found that there is another page for "boot from USB" other than the BIOS setting page. But the page is hidden under the Ubuntu Grub so I did not find it yesterday. Now I can boot with my other USBs. But here comes another problem. When I want to install Win7, it cannot recognize my hard disk. I think probably it is because Ubuntu changed the whole file system. Would you please let me know how to format my hard disk so that I can install Win7 first and double boot an Ubuntu? Thanks!!

---

### Post by oldfred on 2013-09-08
This should say gpt or msdos as well as details on partitions.
Easiest to just copy & paste commands into terminal:

 sudo parted /dev/sda unit s print


 Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

You may want to review link in my signature, but it is a lot of info and the many links have so much data it can be overwhelming for a new user. Even for those who may have understood BIOS & MBR old systems.

---

### Post by sudodus on 2013-09-08
Boot with Ubuntu. Run this command to find out about the partition table (gpt or msdos).

```
sudo parted -l
```

Browse the BIOS meny system to find out about the settings for

- UEFI or CSM (preinstalled Windows 8 is in UEFI mode)
- fast boot (makes it harder* to install Ubuntu)
- secure boot (makes it harder* to install Ubuntu)

*) harder or impossible

---

### Post by fugue2 on 2013-09-08
> **sudodus said:**
> Boot with Ubuntu. Run this command to find out about the partition table (gpt or msdos).

```
sudo parted -l
```

Browse the BIOS meny system to find out about the settings for

- UEFI or CSM (preinstalled Windows 8 is in UEFI mode)
- fast boot (makes it harder* to install Ubuntu)
- secure boot (makes it harder* to install Ubuntu)

*) harder or impossible

Thank you all so much again for your reply. This is the return of the "sudo parted":

```

Model: ATA ST500LM012 HN-M5 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  496GB   496GB   ext4
 3      496GB   500GB   4182MB  linux-swap(v1)

```

and the return of the "[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 
" is:

```

EFI boot on HDD

```


The problem now I have is when I boot to a WIN PE startup USB, I cannot use the partition tools to format my hard disk into what Win7 can recognize. It returns some error like "IDE harddisk not found". The Win PE just cannot detect the harddisk.

[COLOR=#0000ff]Update: I found some solution to similar problem online. Now I am trying to format my harddisk into NTFS in a Ubuntu USB and see what is going on first.[/COLOR]

---

### Post by oldfred on 2013-09-08
You have gpt partitioned drive with UEFI booting. You will have to convert the Windows 7 to a UEFI install. Never done that nor every will,  but posted links above.
All your installs then need to be UEFI, unless you want to totally erase drive, remove gpt partitioning with fixparts and reinstall everything with BIOS and MBR based. You then are back to the issues of 4 primary partitions.

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> You have gpt partitioned drive with UEFI booting. You will have to convert the Windows 7 to a UEFI install. Never done that nor every will,  but posted links above.
All your installs then need to be UEFI, unless you want to totally erase drive, remove gpt partitioning with fixparts and reinstall everything with BIOS and MBR based. You then are back to the issues of 4 primary partitions.


I found that once I delete Ubuntu, I cannot boot with a Win7 USB. It says file error and grub rescue and I can type something after the grub rescue>.

Once I have ubuntu on my laptop, I can boot with the Win7 USB but then the Win7 cannot detect the harddisk...

---

### Post by sudodus on 2013-09-08
You need to change the setting in the BIOS menu from UEFI to BIOS or CSM. Then you should be able to use your old pendrives again.

---

### Post by fugue2 on 2013-09-08
> **sudodus said:**
> You need to change the setting in the BIOS menu from UEFI to BIOS or CSM. Then you should be able to use your old pendrives again.

Thanks! But I cannot find in the BIOS where to change the UEFI setting. The HP BIOS comes with very limited options..

---

### Post by oldfred on 2013-09-08
Someone with HP said the only choice was secure boot on or off. Or it may be called         UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    

But if you want BIOS then you also need to erase drive and convert to MBR(msdos) partitioning so all systems will be in BIOS mode.

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> Someone with HP said the only choice was secure boot on or off. Or it may be called         UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
    

But if you want BIOS then you also need to erase drive and convert to MBR(msdos) partitioning so all systems will be in BIOS mode.


Thanks a lot again. I am still reading your UEFI Installing Tips to understand what they are.  I used the Ubuntu USB to "try Ubuntu" and in the Disks Manger I chose to erase the whole hard disk and format them into fat32, hoping that my Win PE USB will be able to boot and detect my hard disk afterwards. (But there are still 4 hours remaining....) Am I on the right track?


The current situation is: 
--If I have the Ubuntu installed, I can boot with Win7 USB but it says cannot detect IDE hard disk.
--If I unistall Ubuntu, I cannot boot with Win7 USB and it says "files error", "grub rescue>" and all I can do is to boot with the Ubuntu USB.


What I want to do is to install Win7 and then Ubuntu again. (Because under Ubuntu the wireless connection in my laptop is extremely weak and I found no solution during the past week.)


It seems the grub thing came with the Ubuntu (sorry I am newbie and still do not understand what that is) and still lies in my laptop even if I uninstall Ubuntu. So every time when I start the laptop without a Ubuntu installed, it will say grub error and then stop me from booting my Win7 USB.

---

### Post by oldfred on 2013-09-08
I think Windows 7 will only install into NTFS partitions. But did you convert from gpt to MBR, I do not think that would take place unless you force it.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If not converting Windows 7 to a UEFI install, then you will have BIOS which there are many threads and instructions on dual boot. 
The UEFI in my signature is only if you want to use UEFI.

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> I think Windows 7 will only install into NTFS partitions. But did you convert from gpt to MBR, I do not think that would take place unless you force it.

       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

If not converting Windows 7 to a UEFI install, then you will have BIOS which there are many threads and instructions on dual boot. 
The UEFI in my signature is only if you want to use UEFI.


Thanks! You are my life saver.

Would you please let me know what should I do to "convert from gpt to MBR"? So you mean I should first install FixParts and use it to replace gpt with MBR (though I have no idea yet what they are) before installing Win7?

I tried install Ubuntu along with Win8 at the very beginning but it doesn't boot. So I erase the Win8. But from what I have learned online it seems once we have Win7 install, there should be no problem installing Ubuntu along with Win7.

---

### Post by oldfred on 2013-09-08
If you erase the Linux partitions Windows may then install as long as space is unallocated or NTFS. But Windows does not erase the backup gpt partition table. So then you can use fixparts to erase the backup partition table.

You maybe able to erase all partitions and then in gparted change under device, create partition table, advanced make sure it is msdos (MBR). That is usually the default and you have to change to gpt.

Windows 7 typically will use 2 of the 4 available primary partitions, I would just make the rest as the extended. If you let Windows 7 install to entire drive use Windows tools to shrink the Windows partition and immediately reboot into Windows so it can run chkdsk. Do not create partitions with Windows as it may convert to dynamice partitions which does not work with Linux.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

      
 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> If you erase the Linux partitions Windows may then install as long as space is unallocated or NTFS. But Windows does not erase the backup gpt partition table. So then you can use fixparts to erase the backup partition table.

You maybe able to erase all partitions and then in gparted change under device, create partition table, advanced make sure it is msdos (MBR). That is usually the default and you have to change to gpt.

Windows 7 typically will use 2 of the 4 available primary partitions, I would just make the rest as the extended. If you let Windows 7 install to entire drive use Windows tools to shrink the Windows partition and immediately reboot into Windows so it can run chkdsk. Do not create partitions with Windows as it may convert to dynamice partitions which does not work with Linux.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

 Install with screen shots:
[http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT](http://howtoubuntu.org/how-to-install-ubuntu-13-04-raring-ringtail#.UfFD-uHAMfT)
Install options, Do not use erase entire drive unless that is really what you want. That is entire hard drive not just Windows c: "drive".
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

      
 MBR or gpt partitions:
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
Basics of partitions:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)


Words fail to express how much I appreciate your help!

I formated the disk to NTSF in ubuntu but still cannot detect the disk in Win7 USB. But the situation gets a little bit better. Now I can boot the Win7 USB without the Ubuntu installed (will not jump into the grub rescue anymore).

I install the FixParts, and run  sudo fixparts /dev/sda   in the terminal. But it says "This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!"

Then I googled for solutions and followed one of them. I used the gdisk to "destroy" the GPT and then now it seems the disk has nothing at all. Not a GPT nor a MBR. I have no idea what to do now. It seems the partition table is completely empty, as well as my hard disk.

Would you please tell me what to do next?

---

### Post by oldfred on 2013-09-08
If gpt is gone, then you should be able to install Windows in BIOS mode and drive will be MBR(msdos). Windows wants to see either an unallocated space with available primary partition or a primary partition formatted NTFS with the boot flag.

---

### Post by fugue2 on 2013-09-08
> **oldfred said:**
> If gpt is gone, then you should be able to install Windows in BIOS mode and drive will be MBR(msdos). Windows wants to see either an unallocated space with available primary partition or a primary partition formatted NTFS with the boot flag.

I think my Win7 still cannot detect the hard disk. (I edited my previous reply). Here is the result after I print the partition table in fdisk. Does this seem all right?

Disk /dev/sda: 255 heads, 63 sectors, 60801 cylinders

Nr AF  Hd Sec  Cyl  Hd Sec  Cyl     Start      Size ID
 1 00   0   0    0   0   0    0          0          0 00
 2 00   0   0    0   0   0    0          0          0 00
 3 00   0   0    0   0   0    0          0          0 00
 4 00   0   0    0   0   0    0          0          0 00

---

### Post by sudodus on 2013-09-09
If nothing else helps, you can wipe the drive (overwrite it with zeros). Usually it is enough to overwrite the first megabyte. And if you overwrite the first gigabyte, you should also overwrite any traces of the previous uefi partitions. Do not waste time to overwrite the whole drive!

See [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073") and boot from another drive (in your example: boot from the live Ubuntu install CD/DVD/USB drive to wipe the internal HDD or SSD drive.

```
sudo ./mkusb wipe-1
```

if ***mkusb*** is in your current directory to get something like this

```
sudo pv /dev/zero| sudo dd bs=4096 count=256 of=/dev/sd[COLOR=Red]X[/COLOR]
```
or
```
sudo dd if=/dev/zero bs=4096 count=256 of=/dev/sd[COLOR=Red]X[/COLOR]
```
depending if you have installed ***pv*** or not. 

Blocksize bs=4096 makes dd write faster in many computers. count=256 makes it write 1 MB (mibibyte),
because 4096*256=1048576 alias 1 mibibyte.

If you want to overwrite the first internal drive /dev/sda you should replace [COLOR=Red]X[/COLOR] with [COLOR=Red]a[/COLOR]. Be careful, check and double-check, because if you overwrite the wrong drive, you will have problems!

Anyway cut and paste and edit the last character to use it as your command line to wipe the first megabyte of the drive.

After that you should use ***gparted*** to create a new partition table (and if you wish, new partitions)

```
gksudo gparted
```

---

### Post by fugue2 on 2013-09-09
> **sudodus said:**
> If nothing else helps, you can wipe the drive (overwrite it with zeros). Usually it is enough to overwrite the first megabyte. And if you overwrite the first gigabyte, you should also overwrite any traces of the previous uefi partitions. Do not waste time to overwrite the whole drive!

See [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073") and boot from another drive (in your example: boot from the live Ubuntu install CD/DVD/USB drive to wipe the internal HDD or SSD drive.

```
sudo ./mkusb wipe-1
```

if ***mkusb*** is in your current directory to get something like this

```
sudo pv /dev/zero| sudo dd bs=4096 count=256 of=/dev/sd[COLOR=Red]X[/COLOR]
```
or
```
sudo dd if=/dev/zero bs=4096 count=256 of=/dev/sd[COLOR=Red]X[/COLOR]
```
depending if you have installed ***pv*** or not. 

Blocksize bs=4096 makes dd write faster in many computers. count=256 makes it write 1 MB (mibibyte),
because 4096*256=1048576 alias 1 mibibyte.

If you want to overwrite the first internal drive /dev/sda you should replace [COLOR=Red]X[/COLOR] with [COLOR=Red]a[/COLOR]. Be careful, check and double-check, because if you overwrite the wrong drive, you will have problems!

Anyway cut and paste and edit the last character to use it as your command line to wipe the first megabyte of the drive.

After that you should use ***gparted*** to create a new partition table (and if you wish, new partitions)

```
gksudo gparted
```


Thanks so much again for your reply!!

I searched for solution on a Win7 forum and found a program under win PE that automatically fix the partition table into what win7 wants. Now I can install win7 and hopefully dual boot Ubuntu soon. The only defect is I lost 35 GB hard disk space after I ran that program but the outcome is good enough.

Thank you all for your time and help!! I really learned a lot from you.

---

### Post by sudodus on 2013-09-09
Congratulations :KS

I'm not sure you lost 35 GB. It might be used for the NTFS file system journaling (big drive, big journal). Or it is the issue about showing gigabytes (10-base; 1k=1000 ...) or gibibytes (2-base, 1k=2^10=1024 ...).

---

