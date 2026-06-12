---
title: "No boot device found after using boot repair"
date: 2014-01-10
forum: Installation &amp; Upgrades
---

### Post by brendan3863 on 2014-01-10
Dell XPS 15 l521x
Windows 8 and Ubuntu 12.04 64 bit dual boot

The system was dual booting normally using GRUB until yesterday. After shutting down from windows the system began to boot directly to windows (no GRUB screen). I tried doing boot repair from a Live CD. The system now does not boot to an OS and gives an error: no boot device found. I have tried boot repair a few times with no success. All result in the same error.

Here is the link to the latest boot repair output: [http://paste.ubuntu.com/6728288/](http://paste.ubuntu.com/6728288/)

Could someone please help me work through this issue so that my machine dual boots again? Thanks!

---

### Post by oldfred on 2014-01-10
Which version of 12.04 do you have? Probably better to have 13.10. See link below on Dell Precision on XPS15.

You have a backup gpt partition table issue, grub too old issue. And it looks like you ran the "buggy" UEFI rename. I do not think Dell's need that as it is for those systems that modify UEFI to only boot Windows.

 GRUB too old for SecureBoot.

   Reinstall the grub-efi of sda7
GPT:Primary header thinks Alt. header is not at the end of the disk.
GPT:0x57544d68 != 0x575466ef
GPT:Alternate GPT header not at the end of the disk.
GPT:0x57544d68 != 0x575466ef
GPT: Use GNU Parted to correct GPT errors.

     You may want to retry after deactivating the [Backup and rename Windows EFI files] option.

Use a more up-to-date Ubuntu live installer so grub version works.
Download gdisk and see if it suggests fixes to backup partition table. You may have to shrink last partition to make room first.
sudo apt-get install gdisk
      
 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

      
 To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.

      
 Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
Dell UltraBook - Instructions & Details in Post #15 & 16 Devine Shine
[http://ubuntuforums.org/showthread.php?t=2144853](http://ubuntuforums.org/showthread.php?t=2144853)

---

### Post by brendan3863 on 2014-01-10
I am on 12.04.3 and have to use LTS for work.

I will download 12.04.3 and make a new LiveCD and try installing GRUB from that.

Here is the output of 'sudo gdisk -l /dev/sda'

```

GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 1465149168 sectors, 698.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 50A36F6D-4D2C-423C-91D0-4324E4D39C65
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 1465142599
Partitions will be aligned on 2048-sector boundaries
Total free space is 2015 sectors (1007.5 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1026047   500.0 MiB   EF00  EFI system partition
   2         1026048         1107967   40.0 MiB    FFFF  Basic data partition
   3         1107968         1370111   128.0 MiB   0C01  Microsoft reserved part
   4         1370112         2394111   500.0 MiB   2700  Basic data partition
   5         2394112      1136838655   540.9 GiB   0700  Basic data partition
   6      1136838656      1137555455   350.0 MiB   2700  
   7      1137555456      1419364351   134.4 GiB   0700  
   8      1419364352      1444755455   12.1 GiB    8200  
   9      1444755456      1465142598   9.7 GiB     2700  Microsoft recovery part


```

And here is 'sudo fdisk -lu /dev/sda':

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x610d7478

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  1465149167   732574583+  ee  GPT
Partition 1 does not start on physical sector boundary.
```

---

### Post by oldfred on 2014-01-10
gdisk does not seem to show any issues.
And fdisk does not currently work with gpt partitioned drives.

---

### Post by brendan3863 on 2014-01-10
I created a 12.04.3 64 bit live CD and ran boot repair from that. I clicked No at the rename prompt.

Here is the paste bin: [http://paste.ubuntu.com/6729983/](http://paste.ubuntu.com/6729983/)

I still have a no bootable devices when I start the computer. Are there more diagnostic steps I can take? Thanks!

---

### Post by oldfred on 2014-01-11
Boot-Repair says this:
>  The boot of your PC is in Legacy mode. You may want to retry after changing it to EFI mode.



And that is correct. You have no legacy boot options. Both Windows & Ubuntu are installed in UEFI mode.
Ubuntu is not in secure boot mode, so do not turn on secure boot, but turn on UEFI boot.
Only systems that are secure boot configured will be shown if secure boot is on.

Once you get booting, you may want to houseclean some older kernels. I like to keep current and one old one.
       RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[URL="http://ubuntuforums.org/showthread.php?t=898573"]http://ubuntuforums.org/showthread.php?t=898573

[/URL]
 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

[URL="http://ubuntuforums.org/showthread.php?t=898573"]
[/URL]

---

### Post by brendan3863 on 2014-01-13
My current bios settings: 

Add Boot Options: Auto
Secure Boot: Disabled
Load Legacy Option Rom: Disabled
Boot List Option: UEFI

I ran boot repair from a 12.04.3 Live USB Stick. Here is the paste bin: [http://paste.ubuntu.com/6746475/](http://paste.ubuntu.com/6746475/)

When I startup the computer it says: Checking media [Fail] followed by No boot device found. Press any key to reboot machine.

I tried adding /EFI/ubuntu/grubx64.efi as a boot option but the same Checking media and no boot device found error occurred.

---

### Post by oldfred on 2014-01-13
I think the Dell link above did mention something about having Legacy on, but still boot with UEFI.
You have two UEFI systems so there should not be an issue.

Boot-Repair is reporting this.
>  GRUB too old for SecureBoot



I think the first UEFI enabled Ubuntu was 11.10, only 12.04.2 or later had secure boot UEFI capability.  The new 12.04.4 will be out soon and that will have many updates.

But it is strange that Windows is not shown??
>  BootOrder: 0003,2001
Boot0000* UEFI Onboard LAN IPv4
Boot0001* UEFI Onboard LAN IPv6
Boot0002* EFI USB1 PATH1 (Generic Flash Disk)
Boot2001* EFI USB Device
Boot0003* ubuntu



Is your UEFI/BIOS up to date? I thought Dells did not have the 'buggy' UEFI that only boot Windows.

---

### Post by brendan3863 on 2014-01-13
My BIOS is a version behind. A15 came out in December. I have A14 from July. Any idea how I'd install the new BIOS using the exe from Dell even though I can't currently boot to Windows?

---

### Post by oldfred on 2014-01-14
This is before UEFI, but may be similar? I would check Dell's site. They do have a Ubuntu version laptop, so must have a way.
[https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS)

One user with UEFI, Uses WinPE
[http://ubuntuforums.org/showthread.php?t=2180265](http://ubuntuforums.org/showthread.php?t=2180265)

---

### Post by brendan3863 on 2014-01-15
Using a Windows 8 installation disk, I did a refresh of windows. The computer now boots to Windows only without showing an ubuntu or grub efi option in the bios. I have verified that the ubuntu partition is still intact. I ran boot info summary from boot repair using a 12.04.3 live usb stick. Here is the result: [http://paste.ubuntu.com/6756871](http://paste.ubuntu.com/6756871) [Edit: Unlinked pastebin. Did not copy link correctly. This link is not for my system].

I think the next step is to run boot repair again selecting no at the buggy kernel prompt. Another idea would be to install rEFIt to handle the different efi boots. Thought or suggestions where to go from here?

---

### Post by oldfred on 2014-01-15
You are booting with BIOS, so I do not think rEFInd will work. rEFInd is an update to refit which is now old.
Or is link not to your report?

You boot report shows grub in MBR, so that cannot be after a Windows repair as that would have the Windows boot loader in the MBR.
Buggy UEFI only applies to UEFI booting and Dells do not need that.

Not sure what I was looking at, maybe flash drive that gets promoted to sda. But install is UEFI.

---

### Post by brendan3863 on 2014-01-15
I ran boot repair from a 12.04.3 live usb stick and clicked no at the buggy kernel prompt ([http://paste.ubuntu.com/6757039](http://paste.ubuntu.com/6757039)). I rebooted the machine. It loaded grub with options for both ubuntu and windows. I selected ubuntu which loaded perfectly. I shutdown the computer and turned it back on. It then gave the no boot device found error. To summarize, it worked once and then broke again.

---

### Post by brendan3863 on 2014-01-15
Followup to my last post. Immediately after I ran boot repair this was the paste bin: [http://paste.ubuntu.com/6757039](http://paste.ubuntu.com/6757039). I restarted the computer. GRUB loaded correctly. I booted ubuntu 12.04.3. I shutdown the computer and turned it back on. This time grub did not load. I received no boot device found error. I booted to a live stick and created a bootinfo summary (without running boot repair) [http://paste.ubuntu.com/6757338](http://paste.ubuntu.com/6757338). Note the [COLOR=#000000] /FSCK0000.000 files now present. I think this might be causing the problem?[/COLOR]

---

### Post by oldfred on 2014-01-15
Updated above post. Not sure what I was looking at. You do have UEFI boot.

I have not seen any other UEFI system with the fsck files. Not sure if update to Boot-Repair now shows something that was hidden before? But I might just back them up, backup entire efi partition and remove all fsck files.

Some with the older versions of Ubuntu & UEFI have various issues and some have found various work arounds like rebooting a couple of times, full powerdown reboot, or others. Sometimes the one time boot key like f12 (or other depending on your system) works also. 
Many have had fewer issues with 13.10, and soon 12.04.4 will be out although now delayed a couple of weeks.

You can try the buggy UEFI fix. But definitely need the backup of the efi partition. And undo that fix before any Windows update as it will overwrite the renamed shim file that has the Windows efi boot file. You then are back to only booting Windows, but the undo after the Windows update in Boot-Repair may restore an older Windows file and create bigger issues.

Did you turn secure boot back on? 
As Ubuntu is not the signed version, so you will not see it. UEFI will only offer signed installs to boot when secure boot is on.

And grub has a bug on booting Windows from grub menu with secure boot on.

       Remove Duplicate Firmware Objects in BCD and NVRAM
[http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/cc749510%28v=ws.10%29.aspx)
UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

---

