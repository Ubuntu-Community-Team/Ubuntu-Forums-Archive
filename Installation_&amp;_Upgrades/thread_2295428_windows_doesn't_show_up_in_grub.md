---
title: "windows doesn't show up in grub"
date: 2015-09-18
forum: Installation &amp; Upgrades
---

### Post by nigro.orlando on 2015-09-18
Hi! 
I just finished installing Ubuntu Mate alongside a newly installed Windows 7. I think I did everything correctly installing partitions but the grub doesn't see that windows is installed. Does someone sees something weird with the partition that could have caused the problem?

```
sudo fdisk -l

Disk /dev/sda: 238,5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x914ae82e

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1            2048    499711    497664   243M 83 Linux
/dev/sda2       176486400 207734783  31248384  14,9G 82 Linux swap / Solaris
/dev/sda3          704512 176485761 175781250  83,8G  7 HPFS/NTFS/exFAT
/dev/sda4  *    207734784 500117503 292382720 139,4G 83 Linux

Partition table entries are not in disk order.
orlando@orlando-Lenovo-Y50-70:~$ 


```

---

### Post by oldfred on 2015-09-18
Have you run:
sudo update-grub

Did you leave Windows hibernated? Or does it need chkdsk? And to get to Windows to turn it off or repair it, you may have to temporarily install the Windows boot loader, fix Window, then reinstall grub.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

      [/URL]
Grub does not use boot flag. 
And for Windows to boot (or run repairs from repair disk) you must have boot flag on NTFS partition with Windows boot files.

---

### Post by nigro.orlando on 2015-09-18
yes I run update-grub but it didn't help. What you mean leaving windows hibernate? (I'm sorry but I lackf linux-knowledge :( ). 

I can tell you that I first installed windows eliminating the pre-existing OS. Then I installed ubuntu and the installer didn't actually saw windows and I hade to partion it manually. I don't know what that little partition dev/sda1 is doing thare. Could it have something to do with the problem? I'll check the links, thank you for the advice.

---

### Post by oldfred on 2015-09-18
If you installed Windows first, it normally would have made a separate 100MB boot partition. That is not absolutely required, but you then have to move or install the boot files and boot flag to the main install.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by nigro.orlando on 2015-09-18
[http://paste.ubuntu.com/12453224/](http://paste.ubuntu.com/12453224/) 

here it is

---

### Post by nigro.orlando on 2015-09-18
I also followd the instruction after using boot-repair's recommended repair but the grub now is only different looking then it was before, windows is still absent. Before it had mate's graphic interface and now is more "classical" with white text and black screen

---

### Post by oldfred on 2015-09-18
First move boot flag from sda4 to sda3.

It looks like you overwrote the Windows boot partition with a Linux boot partition. Normally you do not need a separate /boot partition for desktop installs. LVM or LVM with encryption does have a separate /boot.

       Vista/7/8 (with 7or 8 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

You are missing the two files that normally are in the Boot partition. You need your Windows repair flash drive or installer to fix it, but boot flag must be on the NTFS partition for repairs to work.

If you run the full set of Windows repairs, it probably will also reinstall the Windows boot loader to the MBR. You just need to use Boot-Repair or live installer to reinstall grub2's boot loader to MBR.

      
 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[http://www.sevenforums.com/tutorials/681-startup-repair.html](http://www.sevenforums.com/tutorials/681-startup-repair.html)
[http://www.w7forums.com/startup-repair-t441.html](http://www.w7forums.com/startup-repair-t441.html)
[URL="https://support.microsoft.com/en-us/kb/927392/"]https://support.microsoft.com/en-us/kb/927392/
[/URL]
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

[URL="https://support.microsoft.com/en-us/kb/927392/"]
[/URL]

---

### Post by nigro.orlando on 2015-09-19
I decided to start from scratch and install again everything from the beginning but this time Installing ubuntu first. I know is not recommended but I needed to use the computer and the installation of windows (which I will use much more rarely) was driving me mad!

I have been trying to install windows since yesterday but I couldn't. When I installed it the first time I did the usb-drive as ntfs and I used unetbootin. In the windows installation panel I couldn't use the partitions (ubuntu was installed) because it said there was a problem with gpd. Since I wanted to format the computer anyway I deleted everything and installed windows on the whole drive. Then I installed Ubuntu and this lead to the problem that I described above. 

now I have been trying to install windows 7 alongside ubuntu but I don't know how to deal with the gpd problem since this time I have to install windows on one spefic ntfs partiion, the one I created from resizing ubuntu. 
I read it depends of the flash drive UEFI bootable configurations and even if I followed a guide on line in order to make it bootable for UEFI I can't make it boot correctly.

This is an other topic of course and I think that for now I won't keep trying but I'll do it some other time. Do you know where should i look to do the procedure correctly? (from putting windows on the USB though the installation of windows and updating of the grub).
Now I have installed ubuntu on the whole drive and I need to resize first but this is the easiest part :). P.S. ubuntu is installed in UEFI.

---

### Post by oldfred on 2015-09-19
If drive is gpt(GUID) then Windows will only install and boot in UEFI boot mode.
Ubuntu can boot with UEFI or Legacy/CSM/BIOS mode from gpt if you have a bios_grub partition.
And Windows only boots from MBR(msdos) partitioned drives with BIOS.

 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

      
 How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html)
[http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx](http://social.technet.microsoft.com/wiki/contents/articles/14286.converting-windows-bios-installation-to-uefi.aspx)
[URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI

[/URL]
 Only 64 bit supported for UEFI boot
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)

[URL="http://gitorious.org/tianocore_uefi_duet_builds/pages/Windows_x64_BIOS_to_UEFI"]
[/URL]

---

### Post by nigro.orlando on 2015-09-20
Thank you very much for the links. I'll check as soon as possible and try to install the system! 

I was also wondering about the possibility to install windows 7 on an external hard drive so that it doesn't mess with the laptops internal and doesn't take gb from linux. Could that be a solution? Would it work smoothly?

---

### Post by oldfred on 2015-09-20
Windows only installs to internal drives. It checks. 
If your external is not  a USB drive and looks like an internal like e-SATA then it may work.

---

### Post by nigro.orlando on 2015-09-20
well, then I have to give up that project and stick with the original idea. 
 
Would this be a good way to go:

1-resize ubuntu
2-format the new space in ntfs (do I have to assign gpt as partition table to the ntfs-partition?)
3-get the iso on a usb drive following the instruction to make it boot in uefi mode
4-install windows on the ntfs partition
5-do the necessary grub repair from a ubuntu live cd 

is it correct? My drive looks like this now:

```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 466743295 465692672 222,1G Linux filesystem
/dev/sda3  466743296 500117503  33374208  15,9G Linux swap

Disk /dev/sdb: 931,5 GiB, 1000170586112 bytes, 1953458176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x076f5785


```

The recommended configurations according to windows say that a default configuration need a system and a msr partition. Is the system the one that I already have? Would windows do something to it?

---

### Post by oldfred on 2015-09-20
The ESP - efi system partition should be shared without issue by both Ubuntu & Windows. The efi boot files are in separate folders. But always a good idea to back up efi partition as well as /home & list of installed apps. Then worst case you can easily reinstall & restore to as now configured.

Windows prefers to have its system reserved. It must be before the first NTFS partition and is 128KB. It is just a working unformatted space for the type of things in MBR formats it used to write just after the MBR (and often conflicted with grub's core.img). Not always used, so not absolutely required.

If booting with UEFI, drive is already gpt partitioned. And you then must boot Windows in UEFI mode. Windows 7 default boot is BIOS, you have to copy to flash drive and move some files around. Do not know details.

---

### Post by nigro.orlando on 2015-09-20
I understand. I have a last question then: do you mean that I have to  create the mbr-space before installing windows or will it windows do it  by itself if I create only one new ntfs partition above my sda2 partition?

---

### Post by oldfred on 2015-09-20
Have not installed Windows since XP in 2006. :)

But I would think if you partition in advance it just uses those partitions, so I would create the unformatted msftres(is flag in gparted) before the NTFS partition. But if you have unallocated space and let it partition then it would create both. Not sure if then it would also try to create another ESP or see that you have one.

---

### Post by nigro.orlando on 2015-09-20
good for your :)!  I myself have also spent many good years without installing windows, it must be since 2010!  Anyway, good, I will try to create the partition myself, thank you very much for your help and all the good advices you gave me.

---

### Post by nigro.orlando on 2015-09-22
Now I did the partitioning and this is how it looks like:

```
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2  191514624 466743295 275228672 131,2G Linux filesystem
/dev/sda3  466743296 500117503  33374208  15,9G Linux swap
/dev/sda4    1050624   1312767    262144   128M Microsoft basic data
/dev/sda5    1312768 191514623 190201856  90,7G EFI System
```

It's weird because in gparted is "efi" first, then"Microsoft base data", "NTFS" and then Linux. Like in the picture that I attached. Which is right? Both are probably but since Windows should be first I wonder if something is wrong

---

### Post by oldfred on 2015-09-22
You cannot have two efi partitions. Remove the boot flag from the NTFS partition.
With UEFI and gpt partition you have a very long GUID that tells UEFI what partition has the efi boot files. Gparted elected to use the boot flag to assign the GUID. gdisk uses ef00 to assign the GUID.

So then a boot flag with UEFI/gpt does not mean the same as a Boot flag with BIOS. With BIOS you do have to have the boot flag on the NTFS partition to install, repair, or boot from.

---

### Post by nigro.orlando on 2015-09-23
right! I didn't notice that problem, thank you, I will remove it.

---

### Post by nigro.orlando on 2015-09-23
Hi again, this installation is really going too far :(. Now that I managed to partition, remove the incorrect flags and make windows7 boot in uefi from usb, the installers freezes at the start. I have read that it could be a problem with the hardware, driver, PCU etc. but I recall managing to install windows once when I did it before installing ubuntu a couple of weeks ago. What is now? One difference is that when I did it then I didn't put windows on the flash drive using the correct procedure for the UEFI booting, in fact I remember the installer complaining about the partition being GPT. This time I followed your guide oldfred and I used that windows program rufus. Could this be a reason for the install to freeze just like that?

---

### Post by oldfred on 2015-09-23
I thought the links in post #9 required Windows 7 installer on flash drive to have files/folders moved around so you have the EFI boot.
Then in UEFI you should have two options to boot flash drive installer, BIOS/CSM/Legacy or UEFI. And you must boot in UEFI mode.

---

### Post by nigro.orlando on 2015-10-04
I managed to solve that issue. Yes you have to move some files around to make it boot as Uefi. But that wasn't the reason of the installer not working. The reason was that even if booting in UEFI, legacy support had to be activated anyway.
Then I got an error message during installation of windows but I read online that it depended by the the USB 3.0 port. I switched to 2.0 and it worked. Now It's finally installed, it works fine and after using boot-repair after installation I also got a perfectly functioning grub. 

Thank you very much oldfred. Now windows is showing up in the grub :). I'll change to solved!

---

### Post by oldfred on 2015-10-04
Glad you figured out issue.

My motherboard seems to have many UEFI settings under a setting that says CSM. I would thing UEFI settings should be separate from the CSM. Since I understand that CSM is a separate chip to offer the BIOS compatibility, that once most systems are UEFI, vendors will convert to UEFI class 3 or no CSM at all, just UEFI.

---

