---
title: "Installing Ububtu 9.10 on an external hard drive"
date: 2010-02-20
forum: Installation &amp; Upgrades
---

### Post by WingATC on 2010-02-20
I looked around on these forums and google and came to no solution so, I decided to make this thread. I'm using Windows XP and after I downloaded and tested out Ubuntu 9.10, I decided I'd like it as a second OS, so I have a few questions:

[LIST]
[*]can I install Ubuntu on my external hard drive (1TB)?
[*]would installing on an external hard drive take away the risks of losing data etc?
[*]If I installed Ubuntu on my external hard drive would it delete any files already on my hard drive?
[/LIST]
Any help would be appreciated :)

---

### Post by MooPi on 2010-02-20
Hello WingATC, and welcome to the forum. Glad you want to make Ubuntu part of your life. Yes you can install Ubuntu to an external drive. Some precautions will need to be taken to ensure your Windows drive stays intact and bootable. First and foremost you must determine if your computer will boot from an external drive. To check this you will need to enter the BIOS of your computer to check. Depending on the brand and type of computer entering your BIOS requires you to reboot and hit a key or combination of keys access.

Second you will need to physically disconnect your internal hard drive from the computer motherboard. either disconnect the data cable or power source to do this. Important to disconnect the power and deplete the charge in the system before you do this. So unplug your computer then depress the power button that starts the computer to relaese any charge in the systems capacitors. The reason I suggest removing your hard drive connections from the system is to keep the Linux boot loader from adding the drive to it's list of bootable drives. If this would happen it may corrupt the master boot record on the drive and cause it not to boot.
After you've completed the install on the External drive you can reconnect the internal drive and set your BIOS to boot from the appropriate drive.
You will need to manually partition the external drive to ensure that you data is safe. I would do this prior to installation. Then when you install direct Ubuntu to install on the empty space.
So if this doesn't scare you away I'll await your happy response that you've just installed Linux to the external drive:D

---

### Post by presence1960 on 2010-02-20
It is not really necessary to disconnect your internal disk. Just install Ubuntu to the external disk and at the ready to install window (see pic below) click advanced and choose to put GRUB on MBR of the external disk. Assuming you have only 1 internal disk then select /dev/sdb to put GRUB on MBR of the external.

You really don't want GRUB on the internal. Putting GRUB on MBR of the external disk will :

1. Allow you to boot right to windows when you boot without the external plugged in. If GRUB is on MBR of the internal disk then you must have the external plugged in at each boot or you will get a GRUB error because the files needed to boot which GRUB points to are on the external disk at /boot/grub.

2. When you boot with the external plugged in GRUB will take over and allow you to boot ubuntu.

Then boot into Ubuntu and open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```At the last window choose your external device (should be /dev/sdb). This will insure whenever you download grub-pc (GRUB2) updates they will go to sdb not sda.

---

### Post by WingATC on 2010-02-21
I think presence1960 has the safer option, so I'll try that :)
> Assuming you have only **1 internal disk** then select /dev/sdb to put GRUB on MBR of the external.I actually have 2 internal drives, but I set my external to always use a certain letter, in this case, my external always takes the J drive. So I select /dev/sdb if I have 1 internal drive, what about if I have 2?
Also, would you're method effect any files already on my external hard drive?

---

### Post by presence1960 on 2010-02-21
> **WingATC said:**
> I think presence1960 has the safer option, so I'll try that :)
I actually have 2 internal drives, but I set my external to always use a certain letter, in this case, my external always takes the J drive. So I select /dev/sdb if I have 1 internal drive, what about if I have 2?
Also, would you're method effect any files already on my external hard drive?

Boot from the LIve CD & choose "try ubuntu without any changes", when the desktop loads open a terminal and run ```
sudo fdisk -l
```that is a lowercase L in -l

Look and see which disk is the external and use that designation. Here is my output from that command:
```

raz@raz-desktop:~$ sudo fdisk -l
[sudo] password for raz: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7408b4a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       21263   170795016    5  Extended
/dev/sda2   *       21264       30401    73400985    7  HPFS/NTFS
/dev/sda5               1        3916    31455207   83  Linux
/dev/sda6            3917        7832    31455238+  83  Linux
/dev/sda7            7833        8354     4192933+  82  Linux swap / Solaris
/dev/sda8            8355       12270    31455238+  83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x05f07bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60801   488384001   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009028

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       65271   524289276   83  Linux
/dev/sdc2           65272       78325   104856255    7  HPFS/NTFS

[COLOR="Red"]Disk /dev/sdh: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00052075

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         131     1052226    b  W95 FAT32
/dev/sdh2             132        1045     7341705   83  Linux
/dev/sdh3            1046        4961    31455270    5  Extended
/dev/sdh4            4962        9964    40186597+   7  HPFS/NTFS
/dev/sdh5            1046        1959     7341673+  83  Linux
/dev/sdh6            1960        4961    24113533+  83  Linux[/COLOR]
raz@raz-desktop:~$
``` 
my external is designated /dev/sdh. Note the designation of your external disk from the output of sudo fdisk -l and use that.

---

### Post by WingATC on 2010-02-21
Alright I'll try that, but would installing Ububtu on my external damage/delete any files already on my external?

---

### Post by darkod on 2010-02-21
> **WingATC said:**
> Alright I'll try that, but would installing Ububtu on my external damage/delete any files already on my external?

It's the same as with internal hdd. You need to have unallocated space into which you can create the ubuntu partitions, either manually or with the guided options.
If you don't have unallocated space you can create it by deleting existing partition, or shrinking existing partition. Which way you choose is entirely up to you and how you want to organize the layout.

Of course, deleting a partition destroys the data on it. Shrinking keeps the data, but you need to have unused space on the partition. And it's always wise to have a backup during any partitioning operation. Just in case the shrinking goes messy.

---

### Post by presence1960 on 2010-02-21
> **darkod said:**
> It's the same as with internal hdd. You need to have unallocated space into which you can create the ubuntu partitions, either manually or with the guided options.
If you don't have unallocated space you can create it by deleting existing partition, or shrinking existing partition. Which way you choose is entirely up to you and how you want to organize the layout.

Of course, deleting a partition destroys the data on it. Shrinking keeps the data, but you need to have unused space on the partition. And it's always wise to have a backup during any partitioning operation. Just in case the shrinking goes messy.

+1

Thanks darko.

---

### Post by WingATC on 2010-02-22
Everything is working fine now, Thanks everyone :)

---

### Post by presence1960 on 2010-02-22
> **WingATC said:**
> Everything is working fine now, Thanks everyone :)

Glad you got it working. Enjoy your dual-boot!

---

