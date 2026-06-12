---
title: "Dual Boot on Separate Hard Disk Drives"
date: 2020-07-03
forum: Installation &amp; Upgrades
---

### Post by Shadius on 2020-07-03
Hi Ubuntu Community,

I'd like to dual boot my existing Ubuntu OS with my existing Windows 10 OS. I have my Ubuntu installed on an HDD and my Windows 10 on an SSD. 

How can I accomplish this dual boot setup where I have these two operating systems on their own drives?

---

### Post by oldfred on 2020-07-03
What is issue?
You say you already have them installed on separate drives? Or which is system is already installed?

Is system UEFI or old BIOS. And is Windows in UEFI or BIOS boot mode?

Generally easier to disconnect or in UEFI/BIOS settings disable Windows drive and install Ubuntu or vice-versa.

For UEFI install info see link in my signature below.

---

### Post by Shadius on 2020-07-04
Hi oldfred, 

I do have them installed on their own drives, but I'd like to be able to select which OS to boot into. 

The system is UEFI. How can I tell if Windows is in UEFI or BIOS boot mode?

---

### Post by tea for one on 2020-07-04
When you power on your PC, there should be a vendor screen with information to press a certain Function key to either access the System Set Up or Boot Device.

For example, I press

**F10** for Boot Device
**F2** for UEFI System Set Up

You will need to find the correct keys for your PC/Laptop.

Anyway, once you have established which key to press for Boot Device, you should then be able to select which drive to boot.

---

### Post by tea for one on 2020-07-04
> **Shadius said:**
> The system is UEFI. How can I tell if Windows is in UEFI or BIOS boot mode?

When you are in Windows 10:-

System Information > System Summary > BIOS Mode (probably UEFI for Windows 10)

---

### Post by oldfred on 2020-07-04
In Ubuntu:
Query to check if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

You need to have both systems in same boot mode, to be able to use grub to dual boot or both as UEFI. But Window fast start up must also be off.

---

### Post by Shadius on 2020-07-08
Hi,

I may be a bit confused. 

Instead of selecting the boot device to boot from by pressing DEL or F2 when my computer boots up, is there a way I can select the OS I want to boot into from a GRUB menu? 

I want Windows as my primary OS and Ubuntu as my secondary OS.

---

### Post by ubfan1 on 2020-07-08
You can set it up so you select Windows or Ubuntu from grub, but only if they have been installed in the same mode.  You can adjust which OS is first (and default) to boot by renaming the files in /etc/grub.d/... to put the Windows script (30_os-prober?) before the Ubuntu script (10_linux).  So something like mv 30_os-prober 05_os-prober should do it.  Another easy way to check the Windows mode, look at the partition type of the disk, if the type is gpt, Windows is in UEFI mode.

---

### Post by Shadius on 2020-07-09
> **oldfred said:**
> In Ubuntu:
Query to check if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD" 

You need to have both systems in same boot mode, to be able to use grub to dual boot or both as UEFI. But Window fast start up must also be off.

Here's my output of the command: 

shadius@shadius-phantom:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Legacy boot on HDD
shadius@shadius-phantom:~$

---

### Post by oldfred on 2020-07-09
Pre-installed Windows since Windows 8 released in 2012 is UEFI with gpt partitioning.
Windows only installs in UEFI boot mode to gpt partitioned drives.

Both Windows and Ubuntu can be installed by a user in the old BIOS/MBR configuration.
But UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch to other mode, or grub can only boot other installs in same boot mode.

If you used or have gpt partitioning on Ubuntu drive with an ESP - efi system partition (FAT32 with boot flag and at least 250MB) you can just reinstall grub when you boot live installer in UEFI mode. Easier with Boot-Repair. Otherwise, you need good backup of /home, perhaps /etc if you changed system settings, and list of installed applications to make it easy to reinstall them and then reinstall in UEFI boot mode.

Most suggest disconnecting Windows drive as Ubuntu's Ubiquity only installs grub to ESP on first drive, usually the windows drive. Most newer UEFI systems let you logically disconnect with UEFI drive settings and changing to disabled. Otherwise see this bug for workaround.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Or you can use Boot-Repair to reinstall grub after install. Grub installs to any drive, it is just Ubiquity that only installs to one drive, even though installer has options (that do not work in UEFI mode). Other distributions using grub2 let you choose drive and they work.

Shows first boot screen, so you know whether you have booted withUEFI or BIOS, although the choice in UEFI boot of flash drive usually says UEFI:XXXX for UEFI boot.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Shadius on 2020-07-09
> **Shadius said:**
> Here's my output of the command: 

shadius@shadius-phantom:~$ [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"
Legacy boot on HDD
shadius@shadius-phantom:~$

Does this mean that my Windows or Ubuntu was installed with BIOS mode and not UEFI mode?

---

### Post by oldfred on 2020-07-09
That says you have booted Ubuntu in BIOS/Legacy/CSM boot mode.
It does not say anything about Windows.

You can check in Windows.

Or if drive is gpt partitioned then Windows has to be UEFI as it only installs in UEFI boot mode from gpt partitioned drives and only in BIOS mode from the old MBR partitioning.

sudo parted -l

---

### Post by Shadius on 2020-07-09
> **oldfred said:**
> Pre-installed Windows since Windows 8 released in 2012 is UEFI with gpt partitioning.
Windows only installs in UEFI boot mode to gpt partitioned drives.

Both Windows and Ubuntu can be installed by a user in the old BIOS/MBR configuration.
But UEFI & BIOS are not compatible. Once you start booting in one mode you cannot switch to other mode, or grub can only boot other installs in same boot mode.

If you used or have gpt partitioning on Ubuntu drive with an ESP - efi system partition (FAT32 with boot flag and at least 250MB) you can just reinstall grub when you boot live installer in UEFI mode. Easier with Boot-Repair. Otherwise, you need good backup of /home, perhaps /etc if you changed system settings, and list of installed applications to make it easy to reinstall them and then reinstall in UEFI boot mode.

Most suggest disconnecting Windows drive as Ubuntu's Ubiquity only installs grub to ESP on first drive, usually the windows drive. Most newer UEFI systems let you logically disconnect with UEFI drive settings and changing to disabled. Otherwise see this bug for workaround.

Posted work around to manually unmount & mount correct ESP during install #23 & #26
 [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)

Or you can use Boot-Repair to reinstall grub after install. Grub installs to any drive, it is just Ubiquity that only installs to one drive, even though installer has options (that do not work in UEFI mode). Other distributions using grub2 let you choose drive and they work.

Shows first boot screen, so you know whether you have booted withUEFI or BIOS, although the choice in UEFI boot of flash drive usually says UEFI:XXXX for UEFI boot.
Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

My Ubuntu was recently upgraded from 18.04 to 20.04. I can't remember what mode it was installed in from since having 18.04. I haven't used it in a while. 

How can I check? Was that the command that you said to use that gave the output of "Legacy on HDD"?

---

### Post by Shadius on 2020-07-10
> **oldfred said:**
> That says you have booted Ubuntu in BIOS/Legacy/CSM boot mode.
It does not say anything about Windows.

You can check in Windows.

Or if drive is gpt partitioned then Windows has to be UEFI as it only installs in UEFI boot mode from gpt partitioned drives and only in BIOS mode from the old MBR partitioning.

sudo parted -l

Here's my output of ```
sudo parted -l
```

```
shadius@shadius-phantom:~$ sudo parted -l
[sudo] password for shadius: 
Model: ATA LITEONIT LCS-256 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  608MB  607MB  primary  ntfs         boot
 2      608MB   256GB  255GB  primary  ntfs


Model: ATA Hitachi HDS72101 (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  983GB   983GB   primary   ext4            boot
 2      983GB   1000GB  17.1GB  extended
 5      983GB   1000GB  17.1GB  logical   linux-swap(v1)


shadius@shadius-phantom:~$ 

```

---

### Post by tea for one on 2020-07-10
According to the output, you do not have an EFI partition in your Windows drive, therefore it looks like you have Windows 10 in Legacy mode.

Can you confirm that you originally started with Windows 7 (or 8) and then upgraded in situ until you reached Windows 10?

---

### Post by oldfred on 2020-07-10
If you run Boot-Repair, DO NOT run the auto fix.
With two drives you want to only use the advanced mode for repairs.
In advanced mode you can choose an install and choose a drive on where to install boot loader.
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You really want a Windows boot loader in MBR of Windows drive and grub boot loader in the MBR of the Ubuntu drive. 
Grub only boots working Windows. And Windows turns fast start up which sets hibernation flag and then grub cannot boot Windows. You have to directly boot Windows, but if you have Windows boot loader in Windows drive you just need to select it in BIOS/UEFI one time boot and fix Windows then boot into grub again.

Best to also have Windows repair/recovery flash drive to fix Windows.
And of course you always need good current backups.

---

### Post by tea for one on 2020-07-10
@oldfred

I do not think that the OP needs boot-repair because there has been no discussion about non booting.
Now that it seems that both systems are in Legacy mode, there is the requirement in post 7 to use grub as the OS selection rather than boot options in the start up UEFI/BIOS screens.

If you use ```
sudo update-grub
``` within Ubuntu, that should pick up the Windows OS.

However, the OP wants Windows as a default with Ubuntu second and I don't know grub intimately enough to help with that request.

My preference would be to use Boot Device Options when powering up the PC but that has been rejected by the OP.

---

### Post by oldfred on 2020-07-10
If OP installs Windows boot loader to Windows drive, then he can set that as default in BIOS/UEFI.
Then whenever he/she wants Ubuntu, use the BIOS one time boot key, often f12 or f10 to choose to boot Ubuntu.
You can change default boot in grub also, but Windows 10 will keep turning on fast start up with updates and then grub will not boot Windows until fast start up turned off.

Multiple ways to change boot order in grub or default boot. Ubfan posted the one where you change order scripts are run.
You can also edit grub default either by number or description. Or manually copy 40_custom to 06_custom and add a Windows entry to that script. Grub processes scripts into grub.cfg in script number order XX_. 

[https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries](https://help.ubuntu.com/community/Grub2/Setup#Specific_Entries)

Even more examples:
[https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub](https://help.ubuntu.com/community/Grub2/Setup#A.2BAC8-etc.2BAC8-default.2BAC8-grub)
find your windows entry in grub.cfg and copy to grub default like this Vista entry - If you edit your windows command use the edited copy as this must match the title exactly:
gedit /boot/grub/grub.cfg
and copy into grub_default  here:
sudo -H gedit /etc/default/grub
GRUB_DEFAULT=0
change to comment # or delete old and add new :
#GRUB_DEFAULT=0
GRUB_DEFAULT="Windows Vista (on /dev/sda1)"
Then do:
sudo update-grub

---

### Post by tea for one on 2020-07-10
> **oldfred said:**
> You can change default boot in grub also, but Windows 10 will keep turning on fast start up with updates and then grub will not boot Windows until fast start up turned off.

Thank you for the informative reply - much appreciated.

Therefore, when selecting the OS, there is a distinct advantage to use UEFI/BIOS Boot Device Options rather than grub when the systems are on **separate** drives.

UEFI firmware is not affected by OS upgrades, albeit Windows or Ubuntu.

---

### Post by oldfred on 2020-07-10
> 
UEFI firmware is not affected by OS upgrades, albeit Windows or Ubuntu. 				

With BIOS that was true. BIOS and operating system were totally separate. But with BIOS updates, it reset to defaults and you often had to redo your settings.

But with UEFI some settings are reset & some are remembered. And operating system can modify some UEFI settings. Windows typically syncs BCD with UEFI boot options and that is why you often have to add another setting to BCS for Ubuntu. 
Other settings are like BIOS and are only changed if you do an UEFI update. But both Windows and now Ubuntu (fwupd) may do UEFI update changing some settings back to defaults and causing issues.

---

### Post by Shadius on 2020-07-10
> **tea for one said:**
> According to the output, you do not have an EFI partition in your Windows drive, therefore it looks like you have Windows 10 in Legacy mode.

Can you confirm that you originally started with Windows 7 (or 8) and then upgraded in situ until you reached Windows 10?

No, I did not do an upgrade install. It was a new Windows 10 install.

---

### Post by dragonfly41 on 2020-07-10
This is what I use with Windows 10 plus an old Ubuntu installation on /dev/sda
and Ubuntu 18.04 on SSD in /dev/sdb

rEFInd .. an alternative boot loader ..

If you can get into Ubuntu install rEFInd thus ..

[https://www.rodsbooks.com/refind/installing.html](https://www.rodsbooks.com/refind/installing.html)

[https://www.rodsbooks.com/refind/](https://www.rodsbooks.com/refind/)

sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind

At the point of installing refind you will be prompted  ..where?
and you point to your EFI partition ..
this can be the Windows EFI partition but if you are canny
for future reference you can have an EFI partition with your external Ubuntu.

Later you can read up how to customise refind.conf.

At bootup you should see reference to /EFI/refind/refind_x64.efi buried with other options and choose that
to skip through options such as Windows > Ubuntu and others which you can later suppress in refind.conf.
I leave them in..

---

### Post by tea for one on 2020-07-10
> **Shadius said:**
> No, I did not do an upgrade install. It was a new Windows 10 install.

That's a surprise that you decided to install in Legacy mode (without an EFI partition) as shown in your post 14.

Anyway, you need to decide how you want to choose your OS when powering on your PC.

[LIST]
[*]Boot using the Boot Device options using the dedicated **function** key of your PC.
[*]
[*]Update grub in Ubuntu and follow oldfred's info in post 18.
[*]
[*]Use the suggestion from dragonfly41 in post 22.
[/LIST]
My preference is still option 1 but I'm sure other users will support their opinions with valid evidence and experience.

---

### Post by dragonfly41 on 2020-07-10
Should also point out the rarely documented option listed in  post#2

[COLOR=#000000]"Generally easier to disconnect"

That is, Windows EFI boot flags can be temporarily disabled (through Gparted) or .. less practical .. cable to Windows drive disconnected.
You are left with only the external drive to boot. But this is a bit messy and requires EFI  partition in external drive.
Some poster in an earlier thread some months back suggested a plug in switch which would isolate either disk (internal/external).
Overall I found from personal experience rEFInd to be easy to switch.

[P.S] Found the link ...

[/COLOR][https://www.amazon.com/Device-Switch-Channel-selector-Module/dp/B01MAX56SA](https://www.amazon.com/Device-Switch-Channel-selector-Module/dp/B01MAX56SA)

---

### Post by Shadius on 2020-07-10
> **tea for one said:**
> That's a surprise that you decided to install in Legacy mode (without an EFI partition) as shown in your post 14.

Anyway, you need to decide how you want to choose your OS when powering on your PC.

[LIST]
[*]Boot using the Boot Device options using the dedicated **function** key of your PC.
[*]
[*]Update grub in Ubuntu and follow oldfred's info in post 18.
[*]
[*]Use the suggestion from dragonfly41 in post 22.
[/LIST]
My preference is still option 1 but I'm sure other users will support their opinions with valid evidence and experience.

I'm not really sure how Windows 10 got installed in legacy mode as I left everything as default when I did the installation. It's strange to me. 

I think I'd like to go with oldfred's option. I was used to the GRUB menu when I only had Ubuntu.

---

### Post by Shadius on 2020-07-10
> **tea for one said:**
> Thank you for the informative reply - much appreciated.

Therefore, when selecting the OS, there is a distinct advantage to use UEFI/BIOS Boot Device Options rather than grub when the systems are on **separate** drives.

UEFI firmware is not affected by OS upgrades, albeit Windows or Ubuntu.

Ahh, I see. 

> **oldfred said:**
> With BIOS that was true. BIOS and operating system were totally separate. But with BIOS updates, it reset to defaults and you often had to redo your settings.

But with UEFI some settings are reset & some are remembered. And operating system can modify some UEFI settings. Windows typically syncs BCD with UEFI boot options and that is why you often have to add another setting to BCS for Ubuntu. 
Other settings are like BIOS and are only changed if you do an UEFI update. But both Windows and now Ubuntu (fwupd) may do UEFI update changing some settings back to defaults and causing issues.

Thank you very much for this information. This changes things now.

---

### Post by Shadius on 2020-07-10
> **tea for one said:**
> That's a surprise that you decided to install in Legacy mode (without an EFI partition) as shown in your post 14.

Anyway, you need to decide how you want to choose your OS when powering on your PC.

[LIST]
[*]Boot using the Boot Device options using the dedicated **function** key of your PC.
[*]
[*]Update grub in Ubuntu and follow oldfred's info in post 18.
[*]
[*]Use the suggestion from dragonfly41 in post 22.
[/LIST]
My preference is still option 1 but I'm sure other users will support their opinions with valid evidence and experience.

Should Windows 10 be running in UEFI mode with an EFI partition? How would I go about correcting it?

---

### Post by oldfred on 2020-07-10
Supposedly you can convert to UEFI, some have said they have done it.
But Windows requires gpt partitioning for UEFI boot, and normal re-partitioning erases drive. Or you need good backups.
Windows also requires totally different set of partitions with UEFI/gpt, so often better just to re-install & restore your data.
If Ubuntu on gpt partitioned drive, you only have to reinstall the UEFI version of grub to convert. But again if MBR, probably easier to backup, re-install & restore from backups. 

BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx) & 
[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions#RecommendedPartitionConfigurations)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

Do not use on Windows drive. Better if drive is just a data drive.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

