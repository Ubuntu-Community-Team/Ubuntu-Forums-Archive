---
title: "No root file system defined"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by fishsticks1907 on 2012-06-17
Hello, im trying to install Ubuntu alongside Windows 7 but i keep getting the "**No root file system defined**" error. i read most of the other post regarding this problem but nothing seemed to help. 

Any help would be great.

---

### Post by ljbaumer on 2012-06-18
I literally just ran into this problem 5 minutes ago :P

I am installing backtrack5 onto my computer but I think the installer should work pretty much the same way. 

When you are in the installer and you get to step 4 (I think) select "Specify partitions manually (advanced)" then click forward and once you decide which partition you want to use for your instalation select it and click "Change..." then once the change menu pops up select "/" under "Mount Point:" and click OK, from there follow through with the installation and it should hopefully all work out for you!

---

### Post by darkod on 2012-06-18
You are getting that message because you are trying to install manually, but you are not specifying any partition to be the root partition (the main system partition).

As already mentioned, if you are trying to use an existing partition, you need to select it in the list, click the button Change below, in the field Use As select ext4 and for mount point select /.

If you need to create new partition(s) for ubuntu, you need to select the unallocated (free) space on the disk shown in the list, and create the partitions you want with the sizes you want. During the creation of the partitions you will have the option to select the filesystem (usually ext4 except for the swap partition), and the mount points.

---

### Post by fishsticks1907 on 2012-06-19
> **darkod said:**
> You are getting that message because you are trying to install manually, but you are not specifying any partition to be the root partition (the main system partition).
 
As already mentioned, if you are trying to use an existing partition, you need to select it in the list, click the button Change below, in the field Use As select ext4 and for mount point select /.
 
If you need to create new partition(s) for ubuntu, you need to select the unallocated (free) space on the disk shown in the list, and create the partitions you want with the sizes you want. During the creation of the partitions you will have the option to select the filesystem (usually ext4 except for the swap partition), and the mount points.
 
i cant change the option, it shows up like this: [www.youtube.com/watch?v=l5cTNg0gs7A](www.youtube.com/watch?v=l5cTNg0gs7A)

---

### Post by fishsticks1907 on 2012-06-19
This is my 5th forum im trying, none of the others could solve it :(

---

### Post by Mark Phelps on 2012-06-19
Could be one of several problems...

Very new PCs, those that come with Win7 preinstalled, are likely to use UEFI, not MBR, partitioning. I'm unfamiliar with this, but I believe that the installer doesn't know how to handle this by default.

Also, preinstalled PCs often come with the maximum of 4 primary partitions already in place.  The installer knows it can't add another, so it does not provide any options.

To get us some info, suggest you boot into the Ubuntu LiveCD, or LiveUSB, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post the info back here.

Without this info, we're only guessing.

---

### Post by darkod on 2012-06-19
Is the partitions list empty like on that video? You never mentioned that, you just said you get the no root filesystem message.

It is important information if the partitions list is empty. :)

Usually that happens if the disk has been used in raid before. Meta data remains are left on the disk which windows ignores but ubuntu doesn't.

If you ARE NOT running raid, boot into live mode with the ubuntu cd, open terminal and try:
```
sudo dmraid -E -r /dev/sda
```

If it asks you to remove raid meta data just confirm. After that the install should work fine.

Note that if you do the above and you ARE running raid, it will destroy your array and probably your data. You install on a raid system in different way. So, do NOT do the above if you are running raid.

---

### Post by fishsticks1907 on 2012-06-19
> **Mark Phelps said:**
> Could be one of several problems...
 
Very new PCs, those that come with Win7 preinstalled, are likely to use UEFI, not MBR, partitioning. I'm unfamiliar with this, but I believe that the installer doesn't know how to handle this by default.
 
Also, preinstalled PCs often come with the maximum of 4 primary partitions already in place. The installer knows it can't add another, so it does not provide any options.
 
To get us some info, suggest you boot into the Ubuntu LiveCD, or LiveUSB, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one), and post the info back here.
 
Without this info, we're only guessing.
 
Okay, i will try(sudo fdisk -lu) this when i get home. btw when i type 
sudo fdisk -l 
i get :
 
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1549f232

Device Boot Start End Blocks Id System
/dev/sda1 * 2048 206847 102400 7 HPFS/NTFS/exFAT
/dev/sda2 206848 1929185279 964489216 7 HPFS/NTFS/exFAT
/dev/sda3 1929187328 1953122303 11967488 7 HPFS/NTFS/exFAT

---

### Post by fishsticks1907 on 2012-06-19
> **darkod said:**
> Is the partitions list empty like on that video? You never mentioned that, you just said you get the no root filesystem message.
 
It is important information if the partitions list is empty. :)
 
Usually that happens if the disk has been used in raid before. Meta data remains are left on the disk which windows ignores but ubuntu doesn't.
 
If you ARE NOT running raid, boot into live mode with the ubuntu cd, open terminal and try:
```
sudo dmraid -E -r /dev/sda
```
 
If it asks you to remove raid meta data just confirm. After that the install should work fine.
 
Note that if you do the above and you ARE running raid, it will destroy your array and probably your data. You install on a raid system in different way. So, do NOT do the above if you are running raid.
 
i believe im running RAID. i will double check when i get home. thanks for the help guys :)

---

### Post by darkod on 2012-06-19
> **fishsticks1907 said:**
> i believe im running RAID. i will double check when i get home. thanks for the help guys :)

If that fdisk result you posted is from the same computer, you can't be running raid since it shows only one disk, /dev/sda.

---

### Post by fishsticks1907 on 2012-06-19
> **darkod said:**
> If that fdisk result you posted is from the same computer, you can't be running raid since it shows only one disk, /dev/sda.
 
Okay, i guess im not running raid. also, heres the result for the "lspci" command (im copying the info from the last forum which couldnt fiqure it out):
 
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS880 Host Bridge
00:02.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (ext gfx port 0)
00:07.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3)
00:09.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 4)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] RS780/RS880 PCI to PCI bridge (PCIE port 5)
00:11.0 RAID [COLOR=blue][FONT=Verdana][FONT=Verdana]bus [/FONT][/FONT][/COLOR]controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 SATA Controller [Non-RAID5 mode]
00:12.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:12.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.1 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0 USB OHCI1 Controller
00:13.2 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: Advanced Micro Devices [AMD] nee ATI SBx00 SMBus Controller (rev 3c)
00:14.2 Audio device: Advanced Micro Devices [AMD] nee ATI SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 LPC host controller
00:14.4 PCI bridge: Advanced Micro Devices [AMD] nee ATI SBx00 PCI to PCI Bridge
00:14.5 USB controller: Advanced Micro Devices [AMD] nee ATI SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 220] (rev a2)
01:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)
02:00.0 Network controller: Atheros [[COLOR=blue][FONT=Verdana][FONT=Verdana]Communications[/FONT][/FONT][/COLOR]]("http://www.linuxquestions.org/questions/linux-newbie-8/question-about-installing-4175412054/page2.html#") Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 [COLOR=blue][FONT=Verdana][FONT=Verdana]Multimedia[/FONT][/FONT][/COLOR] video controller: Conexant Systems, Inc. CX23887/8 PCIe Broadcast Audio and Video Decoder with 3D Comb (rev 04)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
05:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev c0)

---

### Post by darkod on 2012-06-19
This is a raid meta data issue, in my opinion. Since with one disk you can't run raid, no need to worry about that.

Run the command I posted and you're good to go.

---

### Post by fishsticks1907 on 2012-06-19
> **darkod said:**
> This is a raid meta data issue, in my opinion. Since with one disk you can't run raid, no need to worry about that.

Run the command I posted and you're good to go.

Okay i will try it when i get home. But if that doesn't work,
what else could it be?

---

### Post by darkod on 2012-06-19
In some cases an error or corruption in the partition table can make the tools not show any partitions because they can't figure them out.

But in this case I think the raid meta data is your issue. You don't remember using that disk in a raid?

---

### Post by fishsticks1907 on 2012-06-19
> **darkod said:**
> In some cases an error or corruption in the partition table can make the tools not show any partitions because they can't figure them out.
 
But in this case I think the raid meta data is your issue. You don't remember using that disk in a raid?
 
No, i bought it brand new a year and a half ago. Maybe some of the parts weren't new? maybe used?

---

### Post by fishsticks1907 on 2012-06-20
Thank you for everything [darkod]("http://ubuntuforums.org/member.php?u=946366"), its working fine now ;)

---

