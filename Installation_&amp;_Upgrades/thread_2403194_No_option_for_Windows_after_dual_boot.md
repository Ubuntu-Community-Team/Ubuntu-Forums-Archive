---
title: "No option for Windows after dual boot"
date: 2018-10-08
forum: Installation &amp; Upgrades
---

### Post by bluekaterpillar on 2018-10-08
Hello. I am brand new to Ubuntu, and I am trying to install Ubuntu 18.04LTS alongside my Windows 10. I installed Ubuntu successfully, but I can't find an option to choose to boot Windows or Ubuntu on startup; It just goes straight to Ubuntu. Allow me to share with you my journey, and please help me fix my problem.

 
 I fist installed Ubuntu by following the instructions here: [https://www.youtube.com/watch?v=qNeJvujdB-0](https://www.youtube.com/watch?v=qNeJvujdB-0)
 The "Install Ubuntu alongside Windows 10" option did not show up, so I followed the instructions to partition files for "Something Else". My initial free space partition was 80GB, I created a 16GB swap space partition, then left the remainder for \ directory (like is shown int he video).
 
 
 After trying to install, it created a "grub-efi-amd64-signed" package failed to install error. I started the install process again, followed the instructions here ([https://askubuntu.com/questions/1028703/the-grub-efi-amd64-signed-package-failed-to-install-target](https://askubuntu.com/questions/1028703/the-grub-efi-amd64-signed-package-failed-to-install-target)) (second answer down), telling me to create a 1GB EFI System partition as well, and the error did not occur again.
 
 
 I was now able to boot Ubuntu, but unlike in the original video, where starting the computer brings you to a menu which lets you choose Windows or Ubuntu, I was just loaded straight into Ubuntu and was unable to find an option to boot Windows instead.
 
 
 First, I tried following the instructions here: [https://www.youtube.com/watch?v=sueumjgGFkA](https://www.youtube.com/watch?v=sueumjgGFkA)
 My output for "sudo fdisk -l" looks like this:  
 ---------------------------------------------------------------------------------
```
Disk /dev/loop0: 3.7 MiB, 3887104 bytes, 7592 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop1: 2.3 MiB, 2433024 bytes, 4752 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop2: 86.9 MiB, 91099136 bytes, 177928 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop3: 14.5 MiB, 15196160 bytes, 29680 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop4: 140.9 MiB, 147722240 bytes, 288520 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop5: 34.7 MiB, 36323328 bytes, 70944 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop6: 478.2 MiB, 501374976 bytes, 979248 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/loop7: 13 MiB, 13619200 bytes, 26600 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 
 
 
 
 Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x46edf808
 
 
 Device     Boot     Start       End   Sectors   Size Id Type
 /dev/sda1            2048 807214211 807212164 384.9G  7 HPFS/NTFS/exFAT
 /dev/sda2       974987264 976766975   1779712   869M 27 Hidden NTFS WinRE
 /dev/sda3       807215102 974987263 167772162    80G  5 Extended
 /dev/sda5  *    807215104 809213951   1998848   976M ef EFI (FAT-12/16/32)
 /dev/sda6       809216000 841213951  31997952  15.3G 82 Linux swap / Solaris
 /dev/sda7       841216000 974987263 133771264  63.8G 83 Linux
 
 
 Partition table entries are not in disk order.
 
 
 
 
 
 
 
 
 Disk /dev/sdb: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 4096 bytes
 Disklabel type: dos
 Disk identifier: 0x493d9c20
 
 
 Device     Boot Start        End    Sectors   Size Id Type
 /dev/sdb1  *     2048 1953521663 1953519616 931.5G  7 HPFS/NTFS/exFAT
 
 
 
 
 Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: gpt
 Disk identifier: 5A236829-9B5D-474A-847B-D0AD7031BAED
 
 
 Device      Start        End    Sectors   Size Type
 /dev/sdc1      34     262177     262144   128M Microsoft reserved
 /dev/sdc2  264192 1953523711 1953259520 931.4G Microsoft basic data
 
 
 
 
 The backup GPT table is corrupt, but the primary appears OK, so that will be used.
 Disk /dev/sdd: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 4096 bytes
 I/O size (minimum/optimal): 4096 bytes / 33553920 bytes
 Disklabel type: gpt
 Disk identifier: B507B947-051E-4B38-A706-3C8486DFD234
 
 
 Device      Start        End    Sectors  Size Type
 /dev/sdd1      34     262177     262144  128M Microsoft reserved
 /dev/sdd2  264192 7814035455 7813771264  3.7T Microsoft basic data
 
 
 Partition 1 does not start on physical sector boundary.
 
 
 
 
 Disk /dev/sde: 7.2 GiB, 7746879488 bytes, 15130624 sectors
 Units: sectors of 1 * 512 = 512 bytes
 Sector size (logical/physical): 512 bytes / 512 bytes
 I/O size (minimum/optimal): 512 bytes / 512 bytes
 Disklabel type: dos
 Disk identifier: 0x051a159a
 
 
 Device     Boot Start      End  Sectors  Size Id Type
 /dev/sde1  *     2048 15130623 15128576  7.2G  c W95 FAT32 (LBA)
 -----------------------------------------------------------------
 
 
 
 
 then my output for "sudo update-grub" is this:
 ----------------------------------------------------------------------
 Generating grub configuration file ...
 Found linux image: /boot/vmlinuz-4.15.0-36-generic
 Found initrd image: /boot/initrd.img-4.15.0-36-generic
 Found linux image: /boot/vmlinuz-4.15.0-29-generic
 Found initrd image: /boot/initrd.img-4.15.0-29-generic
 Adding boot menu entry for EFI firmware configuration
 done
 --------------------------------------------------------- 
```
 
 
 As you can see, it doesn't see where my windows partition is, and there is no change in how the computer boots.
 
 
 The next thing I tried are the instructions here: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
 Specifically, the "Recommended repair" option; I don't know what to do in the Advance options
 I tried this a few times, and there is the most recent pastebin output: [http://paste.ubuntu.com/p/SBt7mt4t62/](http://paste.ubuntu.com/p/SBt7mt4t62/)
 Again, no changes. However, the final window did say something regarding the boot files being far from the front of the drive.
 
 
 Another thing I have tried is shuffling the boot order of my drives (which includes "ubuntu", the flash drive I used to install it, and the hard drive with my Windows on it), but it has had no effect. Furthermore, when I go back to the BIOS, it always reverts back to having "ubuntu" at the top of the boot order.
 
 
 I'm not sure what to do next, so I've decided to reach out for help to be able to choose which OS to use.

 If all else fails, I would at least like to use Windows again.

UPDATE:


 I figured out how to boot from the flash drive I installed ubuntu on. While there, I retried everything I said above, but with no change.
 
 
 In addition, I tried using GParted based on the instructions in the link provided by boot-repair here: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition)
 However, the layout is different, and I can't figure out how to create a partition at the FRONT of the disk; It says to resize the first partition of the disk that ubuntu is installed on, but that is a Windows partition, and it also says not to edit that partition.

---

### Post by oldfred on 2018-10-08
You must have a new UEFI based system.
But have Windows installed in BIOS boot mode on MBR partitioned drive. But then installed Ubuntu onto MBR drive using UEFI.
UEFI and BIOS are not compatible. Once you start booting in one mode you cannot switch, or grub only boots other systems in same boot mode.

Windows only boots from MBR(msdos) partitioned drives with BIOS boot.
Windows only boots from gpt(GUID) partitioned drives with UEFI boot.
Ubuntu will install in either mode, but UEFI highly recommends UEFI be used on gpt partitioned drives.
How you boot install media for both Windows & Ubuntu UEFI or BIOS, is then how it installs.

You can backup & reinstall Windows in UEFI mode.
Or you can use Boot-Repair's advanced mode and uninstall grub-pc (BIOS boot) and install grub-efi-amd64). That will convert it to BIOS boot.
With multiple drives often best to have each system on separate drive. And you have two SSDs, so speed not an issue.

You also have an issue with boot flags.
With UEFI, the boot flag must be on the ESP - efi system partition.
But with Windows the boot flag must be on the primary NTFS partition with Windows boot files. It looks like your sdb1 is a Windows boot partition?
Windows installs a small boot partition in BIOS mode to the drive set as default in BIOS. So even if you installed to drive seen as sda, but UEFI/BIOS was default booting from sdb, then your Windows boot partition is on sdb.

Grub does not use boot flag.
With BIOS, it looks for the files normally in a Windows boot partition like your sdb1.
With UEFI it looks for the Microsoft folder in the ESP. 
But it only looks for those that match its boot mode.

You may be able to boot in separate boot modes, but only from UEFI boot menu.
But best to have Ubuntu in same boot mode as Windows.

---

### Post by bluekaterpillar on 2018-10-08
sda1 is my Windows partition.

I set the boot flag on that partition using GParted.

I would rather not go through reinstalling Windows again, so I am trying to use Boot-Repair's advanced mode and uninstall grub-pc (BIOS boot) and install grub-efi-amd64.
However I am not sure how to do that.

I tried going into advanced options and checking what looked like the best fit, which was "Place grub into: sda" (under the GRUB location tab", and "Purge GRUB before reinstalling it" (under the GRUB options tab". After hitting Apply, and I followed the instructions. When the window "Configuring grub-pc" poped up in the terminal, i checked only the "/dev/sda" option in the "GRUB install devices:" options.

Here is the post recent pastebin: [http://paste.ubuntu.com/p/gPjhTPbxtz/](http://paste.ubuntu.com/p/gPjhTPbxtz/)

---

### Post by oldfred on 2018-10-08
You are missing a BCD file in sda1, but seem to have one in sdb1? Otherwise you have to use your Windows repair disk to create a new BCD. Linux only can make minor repairs to Windows.

You want to install grub-pc and uninstall grub-efi-amd64. Easiest with Boot-Repair.

Since you have multiple drives, may be better to keep a Windows boot loader on sda, and install grub to sdb. Unless your real Windows boot was thru sdb as only sdb1 has the BCD?
UEFI is better with newer Windows. But two MBRs with different boot loaders will also work. Issue is grub only boots working Windows. And Windows updates may turn fast start up or hibernation back on and then grub will not boot it. Best to use Windows repair disk, but you may be able to directly boot from UEFI/BIOS and f8 into the internal repair console of Windows.

---

