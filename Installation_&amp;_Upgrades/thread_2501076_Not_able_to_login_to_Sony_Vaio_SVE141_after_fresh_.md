---
title: "Not able to login to Sony Vaio SVE141 after fresh install on SSD"
date: 2024-09-22
forum: Installation &amp; Upgrades
---

### Post by pk_rulz on 2024-09-22
Hi 

I had an old Sony Vaio SVE141 E series laptop with Windows 7. It was able to upgrade it to windows 10 which mean that the motherboard supports Win10.

I couldn't find anything related to UEFI in its BIOS so I assume it is a classic MBR BIOS. I changed the harddisk to a brand new Crucial BX500 SSD. I dont prefer to tinker with the old harddisk.

I was able to boot from a USB drive burned with Rufus (in MBR mode) containing Ubuntu 22.04 LTS and install the OS. The process seems to have run successfully. 

On attempting boot from the harddisk the system refused with "No OS Found". I am not sure what went wrong. I am adding some command ops in the hope that it helps

While attempting to debug from the live USB install. These are the outputs

fdisk. Note that sda is the SSD. USB shows up as ssdb
```

fdisk -l
Device       Start       End   Sectors       Size Type
/dev/sda1     2048      4095      2048     1M BIOS boot
/dev/sda2     4096   1054719   1050624   513M EFI System
/dev/sda3  1054720 468860927 467806208 223.1G Linux filesystem

```

efibootmgr
```

$ sudo efibootmgr -v
EFI variables are not supported on this system.

```

Install grub succeeds. I am unable to update grub. Somehow grub seem to be not available in the required path.
```
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: failed to get canonical path of `/cow'.
```

Will be thankful for any help.

A possibility which I was doubting was that the laptop has a buggy bootloader which starts only with windows however my USB booted without any issues so that is unlikely unless the machine allows booting from external devices from any OS but only Windows when it comes to internal harddisk. Is that something seen with VAIO. I understand then reFIND could help but I wanted some expert inputs before putting in more time. Possibly my issue is something more local.

Thanks
PK

---

### Post by tea for one on 2024-09-22
There have been a few occasions where the installer seems to have performed correctly but the PC fails to boot.
This appears to occur with oldish PCS, generally without modern UEFI.

Anyway, given the age of your PC, perhaps Lubuntu or Xubuntu may be worth a shot.
(Lubuntu uses a different installer) 

_Install in Legacy mode to [COLOR="#0000FF"]one[/COLOR] partition_

You could try an installation with only one partition (without a BIOS Boot partition):-
Remove all disks – only the target disk available

Boot into a “Try Ubuntu” live session in Legacy mode
Open terminal and check boot mode
```
[ -d /sys/firmware/efi ] && echo "UEFI" || echo "Legacy"
```
Open Gparted > Devices > Create a msdos partition table on the target disk.
Open the installer
Installation type = Manual Installation (Something Else)
Select free space and click the + sign
Create _one_ Primary partition with Ext4 file system and Mount point = / (system root)
Install Grub bootloader to device not to a partition (e.g sda not sda1)
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP not found, ignore it and continue the installation.
The installer will show that only one partition is to be created and formatted.
Continue the installation
Rarely, you may need to flag the partition as boot or bls_boot

---

### Post by yancek on 2024-09-22
Do you have windows on the old hard disk?  Did you attempt to install Ubuntu to the new SSD?
Your fdisk output shows you have both an EFI partition and a BIOS_boot partition.  You only need one.  The BIOS_boot partition is only used if your disk is GPT and you install in Legacy/MBR mode.  You can determine if the disk is GPT with fdisk.  At the beginning of the fdisk output, you will see disklabel type and it will show GPT if it is a GPT drive and dos if it is has an olde Legacy partition table.

Since your output indicates that EFI is not supported, sda2 (the EFI partiiton) is useless.

The message you got when you ran update-grub means you were trying to update grub on the 'live' usb which will not work as it is read only.  How did you install Grub to sda, specific method you used?  The method to do this is explained on numerous sites including the one below, use chroot.  Ignore the comments on the site about a separate boot partition as you do not have one.

[https://steemit.com/utopian-io/@roj/how-to-install-or-repair-grub-2-with-ubuntu-live-cd-flash](https://steemit.com/utopian-io/@roj/how-to-install-or-repair-grub-2-with-ubuntu-live-cd-flash)

Have you gone into the BIOS on the computer to verify the Ubuntu drive is set to first boot priority?  You could just follow the instruction in post 2 to reinstall if you don't want to do the chrooot reinstall of Grub.

---

### Post by pk_rulz on 2024-09-22
Thank you 'Tea for one'  and Yansek for your inputs. But got the problem fixed. I kept some info in this post so that interested users can make use of it.
I did this before reading your comments. I see that you inputs could have also solved the problem.


TL;DR
For some reason Ubuntu 22 keeps the disk as GPT and not MBR. Older systems which can only handle MBR cant boot from them.
1. Install Ubuntu 20 and upgrade
2. Install Xubuntu
3. Convert disk from GPT to MBR using gdisk and then recover gparted from term or using boot-repair live

It seems the problem was that the disk although has 3 drives listed below it was formated as GPT instead of MBR.
1. boot
2. EFI
3. The main Linux

It was confusing because when I tried to check for efibootmgr, it did say no EFI variables found and so I thought the installation was legacy MBR. But it wasnt. 

While a number of posts say that OS support older systems (the mother board) with only BIOS and UEFI by keeping an unformatted bios.boot drive at the beginning with MBR, atleast in my case it wasnt providing the ability for legacy BIOS motherboard to boot from the SSD.

A post here claimed that Ubuntu 22 does not format a drive to MBR and is probably incapable of doing so. A way out was either to install 20 Upgrade and upgrade or moving to a supported OS like Xubuntu as also listed by teaforone
[https://askubuntu.com/questions/1452315/dual-boot-ubuntu-22-04-in-legacy-bios-mode-mbr-partition](https://askubuntu.com/questions/1452315/dual-boot-ubuntu-22-04-in-legacy-bios-mode-mbr-partition)

I am not sure what the additional boot drive was doing in my case. Possibly a bug or may be I dont understand.

In any case checking with gdisk showed GPT to present and MBR to be protected. Would request any gurus here to explain if protected MBR does allow booting from a legacy BIOS motherboard, because mine didnt.
[https://superuser.com/questions/1250895/converting-between-gpt-and-mbr-hard-drive-without-losing-data](https://superuser.com/questions/1250895/converting-between-gpt-and-mbr-hard-drive-without-losing-data)

Using the steps mentioned in the same post, after booting from a live USB, I converted the disk to MBR from GPT. This caused the bootmgr to be formatted as EFI.
```

Device     Boot   Start       End   Sectors   Size Id Type
/dev/sda1          2048      4095      2048     1M ef EFI (FAT-12/16/32)
/dev/sda2          4096   1054719   1050624   513M ef EFI (FAT-12/16/32)
/dev/sda3       1054720 468860927 467806208 223.1G 83 Linux
```

Trying to install grub after this failed. 

However, when I booted my system again, the SSD instead of saying no OS said entering grub recovery, clearly there was progress. It may be possible to recover grub from gparted recovery but I went for boot-repair-disk

FYI, by now I has started using Ventoy instead of Rufus just to check if Rufus was getting anything wrong.

In boot repair, moved to Advanced >> "Grub Location" >> unchecked separate /boot and /boot/efi and selected 'Place grub in to sda'
It repaired and Voila, system booted.

FYI selecting restore MBR in boot-repair-disk failed saying that no iso is found
After repair it did throw a warning that the repair is at the end of the disk and may not be detected by BIOS which did not make sense since I thought we were writing to the start.

Hope it helps !

---

