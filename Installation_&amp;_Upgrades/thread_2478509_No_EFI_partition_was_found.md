---
title: "No EFI partition was found"
date: 2022-08-28
forum: Installation &amp; Upgrades
---

### Post by Olivares on 2022-08-28
First a description of my PC. I have a 1 Tb dual boot machine with Windows 10 in a 492 Gb partition and Ubuntu in a 438 Gb partition. The boot mode is stated to be BIOS Legacy. A few days ago I attempted an upgrade to Ubuntu 22.04 by an upgrade at the command line. After installation the desktop was not correctly configured, with the top bar missing, the Chrome browser wouldn't open and there was no access to applications other than Libre Office Suite. After a day or so of trying to fix this I gave up and decided my best option was to try reinstalling from a USB. I can't now remember what the outcome was (other than it was unsuccessful), but the upshot is that I decided that I should wipe the operating system from that partition and try installing to a blank partition. I followed instructions in [https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/). I created a root partition 21 Gb, a swap partition with 16Gb and a home partition with the remainder - 434 Gb. Upon clicking 'install' I got the message "no EFI partition was found". I went back to Windows, in DISKPART created a new free space of 100 Mb, but at the 'create partition efi' stage I got the message 'no usable free extent could be found.' I tried in Ubuntu installation to designate free space as efi, but the option to format as FAT32 was greyed out. Attempt to install as is generated the warning "the attempt to mount a file system with type vfat in ... partition #3 at boot/efi failed. You may resume partitioning from the partitioning menu." But I couldn't go back - or forward - and so the only option was to shut down the machine. 

Advice please.

---

### Post by oldfred on 2022-08-28
Are you using gpt partitioning?
The old MBR(msdos) partitioning only allows 4 primary partitions. While Ubuntu may let you install in UEFI mode to MBR, it probably should not.
But gpt is highly recommended by UEFI and Windows only allows gpt with UEFI boot.

Post this:
sudo parted -l

If Windows is in old BIOS/MBR mode, is this a very old system? As Microsoft has required vendors to install in UEFI/gpt mode since 2012.
And if BIOS/MBR, Ubuntu must be installed in BIOS mode also. But if newer hardware, better to reinstall Windows in UEFI mode after good backups.
Older BIOS hardware, not really best for standard Ubuntu anymore.  You typically need a lightweight flavor of Ubuntu.

---

### Post by pbear42 on 2022-08-28
IMHO, it's a bug.  Ubuntu decided to start installing both BIOS and EFI boot loaders when installing in BIOS mode, and then gives this warning if you try to install without the superfluous EFI partition.

In my tests, installing over the warning (without creating an EFI partiton) works fine.  Install completes and system boots.

---

### Post by Olivares on 2022-08-29
Here is output requested. 
[https://drive.google.com/file/d/1n02-IAag6dOvJFTOnqEm9a-TCEA5XgUr/view?usp=sharing](https://drive.google.com/file/d/1n02-IAag6dOvJFTOnqEm9a-TCEA5XgUr/view?usp=sharing) 

The PC was purchased in 2014.

---

### Post by yancek on 2022-08-29
If you run boot repair to get innformation, you should use the Create BootInfo Summary option.  You will get a link to post here so members can view information.  I used the link you posted and could not access it.

>  the attempt to mount a file system with type vfat in ... partition #3 at boot/efi failed 

The quote above would indicate that you are trying to install the Ubuntu / filesystem on the vfat partition so that won't work.  You just install the boot files there.  You should see an option for device for bootloader installation where you can select the vfat/EFI partition.

Windows 10 from a 2014 would probably be an EFI install.  Boot the Ubuntu live usb and select Try Ubuntu and if you get to the Desktop, open aa terminal and run the command below which will show your partitions.  Check to see if you have an EFI partition.

```
sudo fdisk -l
```

I'd suggest running boot repair again and posting the link it gives you, this will be the simplest way to get information.

---

### Post by oldfred on 2022-08-29
Please do not make me sign into Google Drive to help you.
You can just copy & paste terminal output in Code Tags.
How to use Code tags, # in advanced editor
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

And Yancek's request to post link to Summary Report gives even more info, so just partition table output then not required.

---

### Post by Olivares on 2022-08-29
Apologies for the Google drive business. I hadn't occurred to me to access the internet via the "Try Ubuntu" option. Here is the terminal output:

```
 buntu@ubuntu:~$ sudo parted -l
Model: ATA ST1000DM003-1CH1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  368MB   367MB   primary   ntfs
 2      368MB   529GB   528GB   primary   ntfs            boot
 3      529GB   529GB   588MB   primary   ntfs            esp
 4      529GB   1000GB  471GB   extended                  lba
 5      529GB   550GB   21.0GB  logical   ext4
 6      550GB   566GB   16.0GB  logical   linux-swap(v1)
 7      566GB   999GB   433GB   logical   ext4
 8      999GB   1000GB  833MB   logical                   esp


Model: JetFlash TS4GJFV30 (scsi)
Disk /dev/sdb: 4089MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  4089MB  4088MB  primary  fat16        boot, lba



```

---

### Post by Olivares on 2022-08-29
Re recommendation to post Boot Info summary. I ran 'recommended repair' but all it does is refer me to paste2.org, which is not a boot info summary. Do you mean to change partition booted to sda5, the partition for Ubuntu? I didn't think that was the right thing to do as currently there's nothing there.

Thanks for the referral to the 'how to use code tags' page. This was information I needed to know.

---

### Post by oldfred on 2022-08-29
You have Windows in the old BIOS/MBR configuration.
Microsoft has required vendors to install in UEFI/gpt since 2012, so most hardware is UEFI based.

But you cannot mix UEFI & BIOS on same drive. And really should not mix UEFI & BIOS if multiple drives.
And best to use UEFI if UEFI system.

If Windows is BIOS boot, it must be MBR with boot flag on the primary NTFS partition with Windows boot files.
But UEFI required esp,boot flags on the ESP - efi system partition. Only one boot flag per drive, so UEFI & BIOS do not mix.

Also with BIOS boot, you only have one MBR for BIOS boot loader. Only grub lets you choose and normally you can boot Windows from grub.
But grub only boots working Windows. That includes Windows fast startup/hibernation which Windows turns back on with updates.
Then you have to do the bootloader dance, of temporarily installing Windows boot loader to MBR, fix Windows & restore grub to MBR.

UEFI lets you directly boot either Windows or grub from UEFI boot menu, so if grub will not boot Windows, you just have to choose Windows in UEFI boot menu.

If you keep BIOS boot, just make sure to have both a Windows repair flash drive & Ubuntu live installer to update MBR when required.

---

### Post by yancek on 2022-08-30
> Re recommendation to post Boot Info summary. I ran 'recommended repair'  

No, you don't run recommended repair.  If you look at the boot-repair page at the link below, you will  see a small window with recommended repair and Create BootInfo Summary options.  Select the 2nd option there, Create BootInfo Summary.  It will upload the info and give you a link to it which is what you post here.

Since your windows 10 is on an msdos partition and installed in Legacy/CSM mode, you need Ubuntu installed that way also so when you reinstall, make sure your Ubuntu boots in Legacy mode rather than UEFI.r

---

### Post by Olivares on 2022-08-30
I created a Windows recovery USB as recommended; it took 7 hours. I attempted Ubuntu installation again this morning, disregarding the warning about an EFI partition. When installation process completed, all I got was Ubuntu wallpaper, no desktop. Access to Windows restored with Boot Repair. When I ran Boot Repair again, to switch boot up to Ubuntu, I got the message "missing operating system. Reboot and select proper boot device."

Here is output from fdisk -l
```
 ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 2.13 GiB, 2288189440 bytes, 4469120 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 61.96 MiB, 64970752 bytes, 126896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 4 KiB, 4096 bytes, 8 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 163.29 MiB, 171225088 bytes, 334424 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 45.86 MiB, 48091136 bytes, 93928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 400.8 MiB, 420265984 bytes, 820832 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 91.69 MiB, 96141312 bytes, 187776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 46.96 MiB, 49242112 bytes, 96176 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.51 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000DM003-1CH1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x1f9c02ef

Device     Boot      Start        End    Sectors   Size Id Type
/dev/sda1             2048     718847     716800   350M  7 HPFS/NTFS/exFAT
/dev/sda2           718848 1032262772 1031543925 491.9G  7 HPFS/NTFS/exFAT
/dev/sda3       1032775680 1033924607    1148928   561M ef EFI (FAT-12/16/32)
/dev/sda4       1033926654 1953523711  919597058 438.5G  f W95 Ext'd (LBA)
/dev/sda5  *    1033926656 1074942280   41015625  19.6G 83 Linux
/dev/sda6       1074944000 1106192383   31248384  14.9G 82 Linux swap / Solaris
/dev/sda7       1106194432 1951897556  845703125 403.3G 83 Linux
/dev/sda8       1951897600 1953523711    1626112   794M ef EFI (FAT-12/16/32)

Partition 4 does not start on physical sector boundary.


Disk /dev/sdb: 3.81 GiB, 4089445376 bytes, 7987198 sectors
Disk model: TS4GJFV30       
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x004b6600

Device     Boot Start     End Sectors  Size Id Type
/dev/sdb1  *     2048 7987197 7985150  3.8G  e W95 FAT16 (LBA)


Disk /dev/loop8: 284 KiB, 290816 bytes, 568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
ubuntu@ubuntu:~$ 

```

In this installation, boot loader device was set as /dev/sda, per advice in [https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/). Should it have been /dev/sda5 instead?

---

### Post by oldfred on 2022-08-31
You always set boot loader to a drive like sda, never to a partition like sda5.
With UEFI it always finds the ESP - efi system partition and adds a new folder /EFI/ubuntu to ESP.

You have several issues.
It looks like you have UEFI system.
But have Windows installed in 10 year old BIOS boot mode which with Windows requires MBR(msdos) partitioning.
Microsoft has required vendors to install Windows in UEFI boot mode since 2012 on gpt partitioned drives.
Your sdb drive is over 2TB, so has to use gpt. MBR was designed in the early 1980s when KB was large & MB unheard of. So set max at 2TB which would never happen. So now you have to use gpt with GB sized drives. And really only should use MBR with 10 year old systems using Windows.

You cannot mix BIOS boot and UEFI boot on same drive and really should not mix BIOS and UEFI even if multiple drives. If UEFI hardware, you should be using UEFI boot on gpt drives.

Your sda is MBR, so Window install on it is BIOS boot.
So you should not install Ubuntu in UEFI boot mode as UEFI & BIOS are not compatible.
Microsoft requires boot flag on its primary NTFS partition with boot files. Probably your sda1.
But UEFI requires esp,boot flags on ESP - efi system partition. You have sda8  &  sda3 as FAT32 partition for ESP. Ubuntu does let you install in UEFI mode to MBR drives, but really should not.

Use gparted and move boot flag to sda1. If Windows boot loader still in MBR, check that Windows boots & turn off Windows fast startup.
Then use Boot Repair to install the BIOS boot version of grub to MBR.

Better to back up & totally reinstall Windows in UEFI boot mode. And then install Ubuntu in UEFI boot mode. 
Your hardware is UEFI based.
Did you make full Windows backup, not a Windows repair flash drive. Full backup to flash drive is very slow.
But a Windows repair flash drive is small.
Another choice is a Windows PE repair disk, like Windows PE or Hiren&#8217;s BootCD PE , or other similar third party repair ISO.

[https://support.microsoft.com/en-us/windows/recovery-options-in-windows-31ce2444-7de3-818c-d626-e3b5a3024da5](https://support.microsoft.com/en-us/windows/recovery-options-in-windows-31ce2444-7de3-818c-d626-e3b5a3024da5)
[https://www.majorgeeks.com/content/page/5_bootable_isos_to_boot_and_repair_your_computer_for_free.html](https://www.majorgeeks.com/content/page/5_bootable_isos_to_boot_and_repair_your_computer_for_free.html)

---

### Post by tea for one on 2022-08-31
> **oldfred said:**
> Better to back up & totally reinstall Windows in UEFI boot mode. And then install Ubuntu in UEFI boot mode. 
Yes, I fully support this advice.
No further forward after two days,  perhaps 2/3 hours for Windows 10 re-installation (inc. all the config/reboots etc) and 1 hour for Ubuntu = time well spent.
Also, each OS in UEFI mode with GPT will afford you a certain degree of future-proofing?

---

### Post by Olivares on 2022-08-31
I am in favour of converting from BIOS Legacy to UEFI. But two questions. (1) This website [https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/](https://www.maketecheasier.com/convert-legacy-bios-uefi-windows10/) says that if 'BIOS Version / Date' in System Information doesn't say UEFI but only gives name of BIOS version, then I don't have UEFI capability. My System Information doesn't say UEFI, it says 'American Megatrends.' (2) If I am converting to UEFI, do I change something in the ASRock Setup Utility? I have boot options 1 2 and 3, I presume they refer to prioritising first DVD drive, then USB then hard drive? And one of the setup exit options is 'load UEFI defaults.' The mbr2gpt utility the foregoing website refers to apparently is for converting existing installation to UEFI while keeping existing files & folders.

---

### Post by oldfred on 2022-08-31
I have seen  a couple of posts where users tried the conversion and ended up having to do a new install.
Make sure you have good backups.
Your recovery drive may only reinstall in BIOS/MBR mode. Often those types of backups are image based. 

Default partitions from an install are a lot different. Not sure how Windows handles the conversion.
BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations) & 
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)

---

### Post by Olivares on 2022-09-01
Sorry if I'm trying your patience, but I want to have a better idea of what I'm doing before I proceed. I propose to erase everything (files, folders, applications) in Windows and delete partitions with GParted, so that the C Drive is completely blank. Please explain what, if anything, I have to change in the ASRock UEFI Setup Utility. In the Boot menu, there are four boot options and each has these options:
1. SATA: HL-DT-ST DVD RAM
2. UEFI: Built in EFI SHell
3. AHCI PO: ST1000DM003-1CH162
4. UEFI Seagate Backup.

The boot options are set as follows.
Boot option 1: 1
Boot option 2: 4
Boot option 3: 2
Boot option 4: 3.

Do I need to change anything to make the PC boot up in UEFI mode?

---

### Post by oldfred on 2022-09-01
Tea for one posted a nice list, different brands may not have same settings, UEFI varies by brand :
[https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395](https://ubuntuforums.org/showthread.php?t=2467629&p=14061395#post14061395)

Many also require UEFI update to latest available. Often vendors says its only for Windows and sometimes the fixes are really for Linux but not in notes.

Also see link in my signature below.

---

### Post by tea for one on 2022-09-02
> **Olivares said:**
> Do I need to change anything to make the PC boot up in UEFI mode?
Yes - Disable legacy mode in UEFI settings.
If your settings do not allow you to disable legacy mode, you can double check that the USB Installation will be in UEFI mode via the one-time boot menu.
When you boot the PC with the USB installer, you may see two entries:-
[COLOR="#0000FF"]UEFI:[/COLOR]General USB Flash Disk
[COLOR="#FF0000"]USB:[/COLOR]General USB Flash Disk
Choose the option beginning [COLOR="#0000FF"]UEFI:[/COLOR] (i.e. UEFI followed by a colon)
Image attached

Have you backed up all your personal data from both Windows and Ubuntu?

---

### Post by Olivares on 2022-09-05
Thank you everyone for your help. My fresh installation of Windows and Ubuntu in UEFI has been successful and all files & folders restored from backup. Apologies for the delay in letting you know - I got the black screen of death and had to ask for the help of a computer repair man to get back on track.

---

