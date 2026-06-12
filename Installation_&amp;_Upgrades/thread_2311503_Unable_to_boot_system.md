---
title: "Unable to boot system"
date: 2016-01-27
forum: Installation &amp; Upgrades
---

### Post by Dexta_Daps on 2016-01-27
Help, I installed Ubuntu 15.04 alongside my Windows 8 and all I can see now is the grub menu. My laptop has always displayed the boot menu after the Toshiba Logo. 
When I select the HHD/SSD it displays the black screen with "grub>".
When I select the USB it displays the black screen with "grub>".

On either screen type "boot" it tells me I need to loads the kernels first.
when I type "exit" it takes me back to the boot menu. 

I have made a new (my 30th one) Bootable USB with Ubuntu 15.04. I am typing this from withing the system, please help. I've been unable to boot windows since January 2nd, 2016. 

[SIZE=5]**Details:**[/SIZE]

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  1075MB  1074MB  ntfs            Basic data partition  hidden, diag
 2      1075MB  1180MB  105MB   fat32           Basic data partition  boot, esp
 3      1180MB  1314MB  134MB   ntfs            Basic data partition  msftres
 4      1314MB  661GB   660GB   ntfs            Basic data partition  msftdata
 7      661GB   977GB   316GB   ext4
 8      977GB   990GB   12.8GB  linux-swap(v1)
 5      990GB   991GB   523MB   ntfs                                  hidden, diag
 6      991GB   1000GB  9529MB  ntfs            Basic data partition  hidden, diag


Model: TOSHIBA TransMemory (scsi)
Disk /dev/sdb: 15.5GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  15.5GB  15.5GB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo blkid -c /dev/nul
/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="System" UUID="3E9C2E479C2DFA53" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3de3b9ca-0d4a-11e4-8492-a3aaac95da86"
/dev/sda2: UUID="DA2F-2AFB" TYPE="vfat" PARTLABEL="Basic data partition" PARTUUID="3de3b9d2-0d4a-11e4-8492-a3aaac95da86"
/dev/sda3: UUID="96B43177B4315B47" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3de3b9d4-0d4a-11e4-8492-a3aaac95da86"
/dev/sda4: LABEL="TI10699700B" UUID="AEF23C67F23C35C5" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="3de3b9dc-0d4a-11e4-8492-a3aaac95da86"
/dev/sda5: UUID="BCEADC9FEADC576C" TYPE="ntfs" PARTUUID="5c2621ed-6fd5-424b-a62a-3e350560d09a"
/dev/sda6: LABEL="Recovery" UUID="0CBA2DBCBA2DA2E6" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="9e49ed73-481b-11e4-8846-c45444df8f62"
/dev/sda7: UUID="a555fb83-19ae-44d0-b4db-95b73a8f0762" TYPE="ext4" PARTUUID="bda49bf4-568b-4dc7-850f-ddad1af0c5f1"
/dev/sda8: UUID="f10240e3-c19d-455d-9a67-ea16aec6ceae" TYPE="swap" PARTUUID="6492dfd1-f3d1-458e-82e9-5c883d99552b"
/dev/sdb1: LABEL="UUI" UUID="14EA-311F" TYPE="vfat" PARTUUID="06f24787-01"


[http://paste.ubuntu.com/14682291/](http://paste.ubuntu.com/14682291/)

Note: I know very little about command lines and terminal functions. Im a web and app design/developer,  so anything not php or html is foreign to me. Please be as detailed as possible when providing me with instructions. Thank you all

---

### Post by oldfred on 2016-01-27
You may want to try with Secure boot off in UEFI.
From grub you will not be able to boot Windows entry unless secure boot is off, at least for now.
But you should be able to boot from UEFI boot menu or one time key, often f12 on Toshiba.

Toshiba is now like several other vendors and has modified UEFI boot to include description. That is not allowed per UEFI, but perhaps some major operating system vendor has talked to all these vendors since description must be "Windows".

Most dual booting use the fallback or hard drive boot entry. We make that be shimx64.efi and boot hard drive entry not Windows nor ubuntu. The fallback entry is /EFI/Boot/bootx64.efi.
Boot-Repair may automatically copy shimx64.efi to bootx64.efi.
[https://bugs.launchpad.net/boot-repair/+bug/1531178](https://bugs.launchpad.net/boot-repair/+bug/1531178)
'Use the standard EFI file' option in advanced mode.

If not details on commands to copy are in link in my signature.
And other Toshiba users.
       Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)

---

### Post by Dexta_Daps on 2016-01-27
@oldfred If you have the same handle on askubuntu, then I believe you tried helping me over there as well. I cannot turn off secure boot in the UEFI Boot Menu because those options are uneditable in the boot menu. I even did the cold restart then try, and that still didn't work. Thats why I came here.

---

### Post by Dexta_Daps on 2016-01-27
[ATTACH=CONFIG]266993[/ATTACH]   I cannot change turn off secure boot.

---

### Post by oldfred on 2016-01-28
Microsoft requires (at least for now) that vendors configure systems to allow users to turn off Secure Boot.
Since yours is on same screen as passwords, you may have to set those. And if you set UEFI passwords, never lose those as then you may brick system.

You may want to check manual for your system as it should have details.

---

### Post by Dexta_Daps on 2016-01-31
I created the password for both Supervisor and User and it still did not enable the Secure Boot option. what I was able to do is install a new version of Ubuntu unto my laptop along side my inaccesible Windows. I was able to get the boot summary report and it is available here. [http://paste.ubuntu.com/14839277/](http://paste.ubuntu.com/14839277/)

---

### Post by oldfred on 2016-01-31
You are showing two ESP - efi system partitions.
While UEFI spec technically allows more than one, most UEFI implementations just do not work with more than one ESP per device or drive.
Remove boot flag from sda4 with gparted or Disks on Ubuntu live installer.

Usually best to turn off UEFI Secure boot as Boot-Repair has suggested. While Ubuntu will boot with it on, grub menu cannot be used to boot Windows. You can only use UEFI boot menu if secure boot is on.

Toshiba now if like several other like HP & Sony and have started to use description as part of UEFI boot. And of course only valid description is "Windows". 
UEFI has a fall back or default hard drive boot entry /EFI/Boot/bootx64.efi. That often is just a copy of Windows efi boot file but if we make it be a copy of grub2's shimx64.efi then you can boot Ubuntu using the UEFI hard drive entry.

Boot-Repair will copy shim to bootx64.efi, but I am not sure if it creates the hard drive entry in UEFI. Many systems have that already.

Details in link in my signature.
And other Toshiba:
       Toshiba Satellite L15W - Boot only Linux rename UEFI Windows or rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2263473](http://ubuntuforums.org/showthread.php?t=2263473)
Toshiba Satellite P55-A 0[SOLVED] Dual boot Windows 8.1 and Ubuntu 14.10 rename bootx64.efi
[http://ubuntuforums.org/showthread.php?t=2267408](http://ubuntuforums.org/showthread.php?t=2267408)
Toshiba shows BCD entry
[http://ubuntuforums.org/showthread.php?t=2259331](http://ubuntuforums.org/showthread.php?t=2259331)
Can't boot into Ubuntu on a Windows 8 machine (Toshiba P50) Manually copy files cp & mv
[http://ubuntuforums.org/showthread.php?t=2257259](http://ubuntuforums.org/showthread.php?t=2257259)
[http://ubuntuforums.org/showthread.php?t=2261061](http://ubuntuforums.org/showthread.php?t=2261061)

---

### Post by Dexta_Daps on 2016-02-01
I've seen that exact verbiage elsewhere for other peoples issues. Unlike them I don’t know what the first step would be in implementing your solution. What program should I be opening up and once that’s open what should I be clicking on. I'm not computer savvy, I just like Ubuntu's feel. It feels like everyone else that uses this OS is a computer genius. 


[LIST=1]
[*]*How do I* **"Remove boot flag from sda4 with gparted or Disks on Ubuntu live installer."? ***and can I do that on my live session, or do I have to use a usb stick? (this model laptop doesnt have a CD drive)*
[*]**Usually best to turn off UEFI Secure boot as Boot-Repair has suggested.  While Ubuntu will boot with it on, grub menu cannot be used to boot  Windows. You can only use UEFI boot menu if secure boot is on** ... *I've posted picture showing you that I cannot turn this off. Not sure what to make of this*[COLOR=#ff0000][/COLOR]
[/LIST]

---

### Post by oldfred on 2016-02-01
The live installer is either a DVD or flash drive with the Ubuntu install media on it.
You boot live installer in live mode and choose the gparted application.
You can click on the partition and right click to change boot flags.

Microsoft requires vendors to let users change Secure Boot setting. And you have that option, just currently grayed out. So Some other setting, must enable it. If UEFI supervisory password did not work I am not sure what else does.

Have you upgraded UEFI/BIOS from vendor. They also often have issues. You need to go to vendors site and find for you model, in its support area to download the newest UEFI file. And they have instructions there on how to actually install it. Varies by vendor a lot.

Looking back it is a Toshiba hard drive.
What brand/model system do you have?

---

