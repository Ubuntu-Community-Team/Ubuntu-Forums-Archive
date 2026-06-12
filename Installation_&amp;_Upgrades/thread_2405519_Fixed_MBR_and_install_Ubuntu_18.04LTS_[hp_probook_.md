---
title: "Fixed MBR and install Ubuntu 18.04LTS [hp probook 440G3]"
date: 2018-11-07
forum: Installation &amp; Upgrades
---

### Post by mdparvezhossain on 2018-11-07
I may be deleted MBR from my BIOS and now unable to install any OS. 
I want to fix this issues and want to install only ubuntu in my pc. My PC is UEFI enabled maybe. I struck at partitioning part while try to install ubuntu from live usb disk. It says GRUB failed to load. Sometimes while boot the pc it says any OS not found. This type of error message.  
After searching in the forum I fond to submit the latest fdisk status to let the tech guy understand what to do next. 

Here is mine- 
```
$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1864450048 bytes, 3641504 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 86.9 MiB, 91099136 bytes, 177928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 34.7 MiB, 36323328 bytes, 70944 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 2.3 MiB, 2433024 bytes, 4752 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 7BB6CFE4-D28E-4A5A-A8BD-D74B5E410733

Device          Start        End   Sectors   Size Type
/dev/sda1        2048  209717247 209715200   100G Linux filesystem
/dev/sda2   209717248  226494463  16777216     8G Linux swap
/dev/sda3   226494464  658251775 431757312 205.9G Linux filesystem
/dev/sda4   658251776 1090009087 431757312 205.9G Linux filesystem
/dev/sda5  1090009088 1521766399 431757312 205.9G Linux filesystem
/dev/sda6  1521766400 1953523711 431757312 205.9G Linux filesystem


Disk /dev/sdb: 15.2 GiB, 16357785600 bytes, 31948800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x008c3d8c

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1  *     2048 31948799 31946752 15.2G  c W95 FAT32 (LBA)
```

Let me know what should I do next to solve the issue and install ubuntu 18.04

---

### Post by ajgreeny on 2018-11-07
Depending on whether or not you installed using UEFI, you are missing either the ~200MB EFI partition (fat32) or the tiny 1MB bios/grub flagged partition.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for details.

See also **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.	 **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help us find the quickest solution for you.

---

### Post by r_widell on 2018-11-07
I agree with @ajgreeny That you're missing the ESP (EFI System Partition) and also that there's a lot of missing information.

1. Was this disk used in a system before? If so, is there data you want to recover on it?

2. Did you manually partition this disk as part of the install process?

If there's nothing on the drive you want to keep, the solution is easy-- tell the installer to use the entire drive and let it partition the drive correctly.

If there's valuable data on the drive, you can probably recover the old partitions and at least most of the data using testdisk, but I strongly recommend that you spend some time learning about the two partitioning schemes for PC storage drives before using it.

FYI the MBR is not in your computer's BIOS (and from your comment re. UEFI, your computer doesn't have a BIOS).
The MBR is the first sector of a drive partitioned using the {MBR,DOS,legacy} partitioning scheme. Your drive is partitioned using the GPT partitioning scheme (indicated by "Disklabel type: gpt" above). Legacy BIOS firmware doesn't know about GPT partioning. UEFI firmware knows about both MBR and GPT partitioning schemes. GPT drives may have a protective MBR, to guard against non-GPT aware applications inadvertently destroying data on a GPT partitioned drive.

Good Luck,
ron

---

### Post by mdparvezhossain on 2018-11-08
Hello Ron! 
I was a user of windows 10. I had a lot of valuable information stored in my HDD. But, recently I was tired of using windows 10 and decided to install ubuntu. I will be happy to get the data back by recovery process. 

What I want to do is-
I want to install ubuntu as only default and only OS in my machine. If there any process to recover using ubuntu, that would be great for me. 

What I have done so far- 
1. I tried to repair mbr using windows command prompt describe here: [https://neosmart.net/wiki/fix-mbr](https://neosmart.net/wiki/fix-mbr)
Ref to this section: [http://prntscr.com/lfr694](http://prntscr.com/lfr694)

2. I try to install boot-repair from live ubuntu but failed, showing error message that the disk drive has no permission to write or no space available. 
Ref to this methode: [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

3. From the installation process using ubuntu live usb disk, the entire installation process stopped when it comes to partitioning the disk. I spend more than 6-7 hours is this stage but nothing happen.  

4. I also try to repair boot using bootable boot-repair tools. It shows me a success message that my boot-repair is successfully completed but actually nothing happen. 

5. Lastly, I make partition using disk tools from live usb. Where I see that I can set each partition to label NTFS, MBR, FAT, ext4, linux-swap, Linux Home, Linux Root etc.
Then I try to install ubuntu but failed. Everything is just stopped in partitioning part. I can set partition as mount from disk tools but mount point is disable from Gparted. When I mount all of my partition and set the permission to be mounted after rebooting, but, all the partition unmounted after restarting my machine. 

Now, what else I can do now or I am doing all the things wrong? Maybe it's necessary to make the MBR or must be repair-boot first or need to make EFI partition or something else... I don't know the continuous process what to do.

Note: Bootable windows usb disk is not booting now. I mean, I only can boot a ubuntu live disk now. When I try to boot from windows boot disk, it shows me that I don't have any OS in my drive(Ctrl+Alt+Del to Restart). 

Thanks
Parvez

---

### Post by mdparvezhossain on 2018-11-08
> **ajgreeny said:**
> Depending on whether or not you installed using UEFI, you are missing either the ~200MB EFI partition (fat32) or the tiny 1MB bios/grub flagged partition.

See [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for details.

See also **Boot-Repair** in my signature below and follow the instructions there to run the Boot-Info-Script.     **Do not run the default repair just yet** but simply copy back here the pastebin link you get which will show us a lot more about your system and may help us find the quickest solution for you.


[COLOR=#000000]I was a user of windows 10. I had a lot of valuable information stored in my HDD. But, recently I was tired of using windows 10 and decided to install ubuntu. I will be happy to get the data back by recovery process. [/COLOR]

[COLOR=#000000]What I want to do is-[/COLOR]
[COLOR=#000000]I want to install ubuntu as only default and only OS in my machine. If there any process to recover using ubuntu, that would be great for me. [/COLOR]

[COLOR=#000000]What I have done so far- [/COLOR]
[COLOR=#000000]1. I tried to repair mbr using windows command prompt describe here: [/COLOR][https://neosmart.net/wiki/fix-mbr](https://neosmart.net/wiki/fix-mbr)
[COLOR=#000000]Ref to this section: [/COLOR][http://prntscr.com/lfr694](http://prntscr.com/lfr694)

[COLOR=#000000]2. I try to install boot-repair from live ubuntu but failed, showing error message that the disk drive has no permission to write or no space available. [/COLOR]
[COLOR=#000000]Ref to this methode: [/COLOR][https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[COLOR=#000000]3. From the installation process using ubuntu live usb disk, the entire installation process stopped when it comes to partitioning the disk. I spend more than 6-7 hours is this stage but nothing happen. [/COLOR]

[COLOR=#000000]4. I also try to repair boot using bootable boot-repair tools. It shows me a success message that my boot-repair is successfully completed but actually nothing happen. [/COLOR]

[COLOR=#000000]5. Lastly, I make partition using disk tools from live usb. Where I see that I can set each partition to label NTFS, MBR, FAT, ext4, linux-swap, Linux Home, Linux Root etc.[/COLOR]
[COLOR=#000000]Then I try to install ubuntu but failed. Everything is just stopped in partitioning part. I can set partition as mount from disk tools but mount point is disable from Gparted. When I mount all of my partition and set the permission to be mounted after rebooting, but, all the partition unmounted after restarting my machine. [/COLOR]

[COLOR=#000000]Now, what else I can do now or I am doing all the things wrong? Maybe it's necessary to make the MBR or must be repair-boot first or need to make EFI partition or something else... I don't know the continuous process what to do.[/COLOR]

[COLOR=#000000]Note: Bootable windows usb disk is not booting now. I mean, I only can boot a ubuntu live disk now. When I try to boot from windows boot disk, it shows me that I don't have any OS in my drive(Ctrl+Alt+Del to Restart). [/COLOR]

Thanks
Parvez

---

### Post by r_widell on 2018-11-09
I suspect that what happened is that you have a GPT partitioned drive and the ESP (EFI System Partition) was removed. Windows automatically places a protective MBR in logical block 0 of a GPT drive which normally makes it very difficult for applications that are not GPT-aware to muck up your drive (unless you insist).

You said that you tried ajgreeny's Boot-Repais tool. What is the link for the ubuntu pastebin it created?
That is probably irrelevant now, because the first order of business is to try to recover some data from the drive.

Boot from the ubuntu liveDVD and open a terminal window. Then issue the command ```
sudo apt-get testdisk
```.
Testdisk is the best partition recovery tool I know of and does an amazing job of making hard drive usable again after the partition table gets hosed.
But it's not designed to be foolproof. Wikipedia has good articles on MBR and GPT partitioning schemes, read and understand them fully before you do anything else.

Testdisk does NOT have a GUI, it is terminal window-only. You do things with the arrow, tab, enter and escape keys (and a few others, depending on the stage you're at). After the installation is complete, enter ```
sudo testdisk
``` in the same terminal window you used to install it.

It will start by having you select a drive. Since you only have one in your system, it should already be selected
It will then ask for the partitioning scheme, select GPT.
Accept the defaults for C/H/S.
After it shows how the current partition table is set up, let it do a deep scan.
This will take a looooong time. It's reading every byte in every sector of the drive. It's looking for partition headers of partitions that are not in the partition table so the partition table can be rebuilt correctly.
When it's done it will show what it thinks the partition table could/should be. There may well be partitions that overlap. When that happens you may (and should) choose which partition table entry you want to keep.

I expect that you had at least 3, but more likely 4, or even 5 partitions on your drive. Microsoft requires the ESP (100-200 MB), an MSR (Microsoft System Reserved, 128 MB), and a Microsoft Basic Data partition (where the OS and user files are located) which occupies most of the drive. There's most likely also an OEM diagnostic partition, or at least a recovery partition where there's a compressed image of the as-shipped OS to return the machine to an out-of-the-box state, There could also be a partition holding a WinRE recovery environment. These last optional partitions will likely be reasonable small, 4-8 GB or less.
Knowing what to expect will help guide you in knowing what to keep.

Once you've made your choices, you now have the option of writing the new partition table to the disk. Up to this point, no changes have been made to the drive so you can cancel your way all the way back out of testdisk and try again if nothing looks right.

If you don't understand what you see on the screen, don't write to the drive, Just back out and find a guru in your area that can help you interpret what testdisk recommends.

You could also provide screenshots and we'll try to help you here, but that will obviously be a much slower process.

Good luck,
ron

---

