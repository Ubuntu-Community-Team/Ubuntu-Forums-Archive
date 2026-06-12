---
title: "Windows 10 &amp; Ubuntu 17.04 Dualboot Grub Missing"
date: 2017-05-20
forum: Installation &amp; Upgrades
---

### Post by mdobrenko on 2017-05-20
I previously installed a stand-alone copy of Windows 10 on my Microsoft Surfacebook. I intend to set up Ubuntu dual-boot alongside it. Unfortunately, after installation following these instructions ([https://itsfoss.com/no-grub-windows-linux/](https://itsfoss.com/no-grub-windows-linux/)) Windows still boots over Ubuntu -- the GRUB loader is ignored? 

I have tried the following:

 - Running boot repair from Live Ubuntu USB. This apparently runs and does some things, which prevents both Windows and Ubuntu from booting altogether -- gets stuck with the Surfacebook loading animation, screen flashes, goes into UEFI.
 - Going into windows and trying to change the boot according to this post: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
 - Installing Ubuntu by itself -- for some reason, the GRUB refuses to show up, and no boot-repair operations are of any help. 

Here is the info output of my boot-repair program: [https://pastebin.com/N1J4H9eF](https://pastebin.com/N1J4H9eF)
Attached is also a screenshot of my GParted of the SSD (only one on my Surfacebook).

Any help would be greatly appreciated. Been wrestling with this problem for more than a few days now, and just can't figure it out... would prefer not to do backend development on Windows!

---

### Post by oldfred on 2017-05-20
This has info on install on Surface Boot but using MicroSD card.
[https://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798](https://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798)

You may just need to do the recommendation at bottom of Boot-Repair's report.
Editing of BCD is one of many work arounds for systems that do not want to directly boot an Ubuntu entry in UEFI.

If you run Boot-Repair it will copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi. That then is a backup or fallback way to boot.
Some also require you to add an entry into UEFI for that entry.
More details in link in my signature and:
 Copy shimx64.efi to /EFI/Boot/bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2247186](http://ubuntuforums.org/showthread.php?t=2247186)
Boot-Repair should automatically do copy file with 'use standard EFI file':
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)
Sony, HP & others:
[http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789](http://askubuntu.com/questions/486752/dual-boot-win-8-ubuntu-loads-only-win/486789#486789)

---

### Post by mdobrenko on 2017-05-20
Tried running boot-repair first, and then it did as stated before; stopped booting to windows, nor did it start booting into Ubuntu.
Installed Windows 10/Ubuntu all over again using the same process as before, booted into windows to perform the [FONT=arial]bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi change, and that did not work.
What is the next step?

EDIT: Ran boot-repair after the fact, and here is the output:

[https://pastebin.com/DAQ0bxSR](https://pastebin.com/DAQ0bxSR)I am

 I am guessing I need to add the UEFI entry myself? Unfortunately, I cannot boot into Windows 10 anymore to run the BCD. Is there a different way to do so?[/FONT]

---

### Post by oldfred on 2017-05-20
This always causes issues. You have to turn Windows fast start up off.
>  Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.) 

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Can you boot Windows from UEFI boot menu and immediately press  f8 to get into its internal repair console.
Otherwise you should make Windows repair disk so you can repair it instead of always reinstalling.
       
 Windows 8 UEFI fixes, if no repair flash drive you may be able to download Window installer and use it.
[URL="http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader"]http://superuser.com/questions/460762/how-can-i-repair-the-windows-8-efi-bootloader
[/URL]
 Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options) 

Check entry is there.
sudo efibootmgr -v  

 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi'  -d /dev/sdX -p Y
sdX is drive, Y is efi partition example for sda2 

But in your case you have the new NVMe drive so probably like this with your ESP as partition 2?
sudo efibootmgr -c -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/nvme0n1 -p 2 
Then confirm entry:
sudo efibootmgr -v

---

### Post by mdobrenko on 2017-05-21
Unfortunately cannot boot straight into windows -- I have to use the repair disk.

In any case, running sudo efibootmgr -v:
```

BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0001,0000,0002
Boot0000* Internal Storage    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)SDD.
Boot0001* USB Storage    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)USB.
Boot0002* PXE Network    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(50670071-478f-4be7-ad13-8754f379c62f)PXE.
Boot0003* MsTemp    PciRoot(0x0)/Pci(0x14,0x0)/USB(0,0)/USB(0,0)/HD(1,MBR,0x4294967177,0x800,0x3b8200)

```


Running the efibootmgr: sudo efibootmgr -c -L "UEFI hard drive" -l "\EFI\Boot\bootx64.efi" -d /dev/nvme0n1 -p 2
```
could not prepare Boot variable: No space left on device
```

EDIT: I found this while searching around, but it does bring some more information in. Running sudo efibootmgr -c shows:
```

GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
GUID Partition Table Header signature is wrong: 0 != 5452415020494645
Could not prepare Boot variable: No space left on device

```

---

### Post by oldfred on 2017-05-21
Did you make sure this exists before running the efibootmgr? \EFI\Boot\bootx64.efi

If partition table issues, best  to have backup of partition table.
If fdisk/sfdisk from 16.04 or later you can backup Partition Table with fdisk, older versions do not support gpt.
       sudo sfdisk -d /dev/sda > PTsda.txt 
    
For repairs I prefer gdisk:
What does gdisk show?
 sudo gdisk -l /dev/sda 

GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)
[http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/sgdisk-walkthrough.html) 

You can run p to print, q to quit or w to update/refresh if it looks good.
      sudo gdisk /dev/sda
Command (? for help): 

 [http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by mdobrenko on 2017-05-21
How can I verify that it exists? I am booted from live USB, so how do I access the SSD and the Linux installation to check if \EFI\Boot\bootx64.efi exists?

sudo sfdisk -d /dev/sda > PTsda.txt:
```

label: dos
label-id: 0x0032d389
device: /dev/sda
unit: sectors

/dev/sda1 : start=        2048, size=     3899904, type=c, bootable

```
sudo gdisk -l /dev/sda:
```

ubuntu@ubuntu:/boot$  sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. 
***************************************************************


Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
Disk /dev/sda: 3901952 sectors, 1.9 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 3B13CEC8-B511-41ED-908A-D14F9D6339A1
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3901918
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         3901951   1.9 GiB     0700  Microsoft basic data

```

Is there any way to simply reset everything (BIOS, UEFI settings, etc) when installing Windows 10? I had Ubuntu running as dualboot in the past, but for some reason it just doesn't work now. I wonder if it might not be easier to just re-install, wipe settings completely, and then try installing Ubuntu?

---

### Post by oldfred on 2017-05-21
That is saying you have BIOS/MBR for Windows.
Windows only boots in BIOS mode from MBR partitioned drives.
And only in UEFI mode from gpt partitioned drives.
Ubuntu can boot in either mode from gpt if supporting partitions are on drive, bios_grub for BIOS and ESP - efi system partition for UEFI.

Was Windows 10 originally installed on this system, or did you install it or upgrade it from Windows 7.
Windows 10 from vendors must be in UEFI/gpt, but upgrades from Windows 7 probably are BIOS/MBR. 
If installed yourself it totally depends on whether you booted installer in BIOS or UEFI mode as how you boot install media, it then how it installs for both Windows & Ubuntu.

And if BIOS then it makes sense you have to repair Windows to boot. With BIOS you only have one MBR, so only one boot loader can be in control. Grub will allow booting Windows, but Windows has to be working. And that means no chkdsk required and no hibernation nor fast start up. Often Windows turns that back on, so you need a Windows repair disk to restore Windows boot loader to MBR to directly boot hibernated Windows 10.
With UEFI all systems install boot loaders into ESP - efi system partition. Kinda like having many MBRs, and then from UEFI you can always choose which system to boot.

If you have UEFI hardware, probably better to have operating systems installed in UEFI boot mode. There are advantages to UEFI and gpt partitioning over the 35 year old BIOS/MBR configuration which goes back to the original IBM PC with many fixes over the years.

Since not using UEFI, efibootmgr will not work.

---

### Post by mdobrenko on 2017-05-21
I am not quite sure I understand why this happens... I used Rufus to make the bootable image, and then selected "GPT partition scheme for UEFI" (this time around) and it still shows the same thing -- MBR only.
Where is it deciding to use the BIOS/MBR configuration?

---

### Post by oldfred on 2017-05-21
When you boot install media. 
It only installs in mode you boot install media UEFI or BIOS.

In UEFI you typically have two boot options when Secure Boot is off. (if on then only UEFI Secure Boot).
You should see UEFI:flash and flash where flash is the name or label of the flash drive.

And Windows 7 DVD is BIOS only, but newer Windows versions offer both. 
Windows 7 has to be converted to flash drive and .efi file created by moving & renaming some files to make it UEFI bootable.

With Ubuntu you get two different screens, so you also can tell on first screen you see which way you have booted.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 

Not sure with Windows as never installed to UEFI from scratch.

---

### Post by mdobrenko on 2017-05-21
When I install, I get the black UEFI screen -- so this would suggest it is working as intended, right?

---

### Post by oldfred on 2017-05-21
For Ubuntu yes.

I normally suggest installing Windows first as it wants lots of extra partitions, now with UEFI/gpt. But if it uses entire drive only use Windows to shrink the NTFS partition and reboot immediately as it has to run chkdsk after resize. Make sure fast start up is off as Windows will keep turning it on with updates.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)
[https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/windows-recovery-environment--windows-re--technical-reference)
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Order on drive is important: msftres
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition) 

And I prefer to use gparted to create my Linux partitions as I typically want more than just / (root) & swap (no swap with 17.04).
And use Something Else to install choosing (change) my previously created / (root) partition.

---

### Post by mdobrenko on 2017-05-21
Ended up trying to install Ubuntu alone  (Wiped the drive completely first) by specifying my own partitions. The USB boots in UEFI mode.
Why is it that running gdisk on /dev/sda1, having removed Windows & declared my own partitions still leaves it as an MBR?

---

### Post by oldfred on 2017-05-21
If you declared your own partitions and it was already MBR, then I am not sure what UEFI installer does.

I always partition in advance, typically with gparted.
But first thing you have to do is convert to gpt.
       I have created my gpt partitions with gparted. Under device, create partition table, advanced, choose gpt not the default msdos (MBR) partitioning. 

 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary (no logicals):
gpt: 300-500 MB efi FAT32 w/boot flag (ESP for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 or 2 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30 to 50GB just use / not separate /home or standard install.


[LIST=1]
[*]20-25+ GB Mountpoint / primary or logical beginning ext4 
[*]all but 2 GB Mountpoint /home logical beginning ext4 
[*]2 GB Mountpoint swap logical 
[/LIST]
    Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
suggested partitions for just Ubuntu on 3TB drive.
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
Another advanced suggestion from TheFu with Multiple / (root) - Post #5 similar to what I actually do
[http://ubuntuforums.org/showthread.php?t=2170308](http://ubuntuforums.org/showthread.php?t=2170308)
[http://ubuntuforums.org/showthread.php?t=2021534](http://ubuntuforums.org/showthread.php?t=2021534)
UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu)
[http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme](http://askubuntu.com/questions/336439/any-problems-with-this-partition-scheme)
[http://askubuntu.com/questions/461394/how-to-partition-ssdhdd](http://askubuntu.com/questions/461394/how-to-partition-ssdhdd)

I prefer a /mnt/data over /home as separate partitions. But I typically have multiple 25GB / (root) partitions for various test installs.
And I do not want /home settings in each. And /mnt/data requires a bit more knowledge to mount in fstab, set ownership & permissions and link data into /home. Where a /home partition does all that as part of install, but gives the option of a separate / and somewhat easier reinstall.

---

