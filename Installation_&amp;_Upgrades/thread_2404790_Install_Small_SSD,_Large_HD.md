---
title: "Install: Small SSD, Large HD"
date: 2018-10-28
forum: Installation &amp; Upgrades
---

### Post by webmanoffesto on 2018-10-28
I have a System 76 Meerkat. It came with a small SSD (32GB) and I put in a large spinning disk HD.

I'm booting into Lubuntu on a Multisystem Flash Drive [http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)
I think I started using Multiysystem because I can create the whole thing on an Ubuntu computer. 

1. Please tell me how to resolve the below UEFI "warning message".
UEFI Warning Message
```

This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.
If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.

```

2. How do I make sure that Lubuntu puts uses the partitions correctly. 
Should root be on the SSD?
I want the OS to go on the SSD.
I want Swap on the Spinning Disk Drive.
I want Home to be on the Spinning Disk Drive

Ubuntu Gnome Install let's me choose
Device for boot loader instalation
I can choose 
/dev/sdb ATA TS32GMTS800 (32.0 GB)

```

ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -l
Disk /dev/loop0: 1.3 GiB, 1350991872 bytes, 2638656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6bb2835b


Device       Boot Start     End Sectors  Size Id Type
/dev/loop0p1 *        0 2638655 2638656  1.3G  0 Empty
/dev/loop0p2      14348   19019    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/loop1: 1.2 GiB, 1295798272 bytes, 2530856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7A9D8147-A8D7-4E9B-A43E-868363E24EE3


Device        Start      End  Sectors  Size Type
/dev/sdb1      2048     4095     2048    1M BIOS boot
/dev/sdb2      4096 54142975 54138880 25.8G Linux filesystem
/dev/sdb3  54142976 62531583  8388608    4G Linux swap


Disk /dev/sdc: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x686a6515


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 62529535 62527488 29.8G  b W95 FAT32
ubuntu-gnome@ubuntu-gnome:~$


ubuntu-gnome@ubuntu-gnome:~$ sudo fdisk -l
Disk /dev/loop0: 1.3 GiB, 1350991872 bytes, 2638656 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6bb2835b


Device       Boot Start     End Sectors  Size Id Type
/dev/loop0p1 *        0 2638655 2638656  1.3G  0 Empty
/dev/loop0p2      14348   19019    4672  2.3M ef EFI (FAT-12/16/32)


Disk /dev/loop1: 1.2 GiB, 1295798272 bytes, 2530856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sdb: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 7A9D8147-A8D7-4E9B-A43E-868363E24EE3


Device        Start      End  Sectors  Size Type
/dev/sdb1      2048     4095     2048    1M BIOS boot
/dev/sdb2      4096 54142975 54138880 25.8G Linux filesystem
/dev/sdb3  54142976 62531583  8388608    4G Linux swap


Disk /dev/sdc: 29.8 GiB, 32015679488 bytes, 62530624 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x686a6515


Device     Boot Start      End  Sectors  Size Id Type
/dev/sdc1  *     2048 62529535 62527488 29.8G  b W95 FAT32


ubuntu-gnome@ubuntu-gnome:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
loop1    7:1    0   1.2G  1 loop /rofs
sdb      8:16   0  29.8G  0 disk
&#9500;&#9472;sdb2   8:18   0  25.8G  0 part
&#9500;&#9472;sdb3   8:19   0     4G  0 part [SWAP]
&#9492;&#9472;sdb1   8:17   0     1M  0 part
loop0    7:0    0   1.3G  0 loop /cdrom
sdc      8:32   1  29.8G  0 disk
&#9492;&#9472;sdc1   8:33   1  29.8G  0 part /isodevice
sda      8:0    0 931.5G  0 disk
    
=========================
UUID
https://liquidat.wordpress.com/2013/03/13/uuids-and-linux-everything-you-ever-need-to-know/


ubuntu-gnome@ubuntu-gnome:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 11 Oct 27 19:18 2017-08-01-12-14-19-00 -> ../../loop0
lrwxrwxrwx 1 root root  9 Oct 27 19:18 9090e43b-ea5a-440f-b207-8429f2bedfc5 -> ../../sda
lrwxrwxrwx 1 root root 10 Oct 27 19:18 b7ac1b9e-106f-4dd4-8dee-28ed042623c7 -> ../../sdb2
lrwxrwxrwx 1 root root 10 Oct 27 19:18 dc9c43cf-c32e-44e0-8fbe-406603792c0b -> ../../sdb3
lrwxrwxrwx 1 root root 10 Oct 27 19:18 FFE2-49C6 -> ../../sdc1


buntu-gnome@ubuntu-gnome:~$ blkid
/dev/sdc1: LABEL="MULTISYSTEM" UUID="FFE2-49C6" TYPE="vfat" PARTUUID="686a6515-01"


/dev/loop0: UUID="2017-08-01-12-14-19-00" LABEL="Ubuntu-GNOME 16.04.3 LTS amd64" TYPE="iso9660" PTUUID="6bb2835b" PTTYPE="dos"


/dev/loop1: TYPE="squashfs"


/dev/sda: LABEL="WD1TBHD" UUID="9090e43b-ea5a-440f-b207-8429f2bedfc5" TYPE="ext4"


/dev/sdb2: LABEL="Ubuntu" UUID="b7ac1b9e-106f-4dd4-8dee-28ed042623c7" TYPE="ext4" PARTLABEL="primary" PARTUUID="54112719-6aa1-4b64-bde9-bbcade3f4f1c"


/dev/sdb3: UUID="dc9c43cf-c32e-44e0-8fbe-406603792c0b" TYPE="swap" PARTLABEL="primary" PARTUUID="a6266739-5474-4bc5-9005-e2b6fe65e7c7"

```

---

### Post by oldfred on 2018-10-28
Your bios_grub partition is only for BIOS/CSM/Legacy type installs.
For UEFI install you need an ESP - efi system partition which is FAT32 with boot and/or esp flags.

Is the installer then seeing bios_grub and not ESP, so thinks you have BIOS installs?
I normally put both an ESP & bios_grub as first two partitions of every drive including larger flash drives and all drives are now gpt partitioned.

I would put ESP & / (root) on SSD and /home on HDD.

New versions of Ubuntu do not use swap partition, but a swap file of 2GB. But if swap partition found it will use it. 

If using UEFI, you need drives to be gpt partitioned. But if only installing Ubuntu, you can use gpt and BIOS boot if you have the bios_grub partition.
It is only Windows that must have MBR for BIOS boot or gpt for UEFI boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by webmanoffesto on 2018-10-29
> **oldfred said:**
> Your bios_grub partition is only for BIOS/CSM/Legacy type installs.
For UEFI install you need an ESP - efi system partition which is FAT32 with boot and/or esp flags.

Okay, so I need an ESP, that's an EFI System Partition. That means I will need to format that partition as FAT32 and I will need to set it to have Boot and/or ESP flags.

When I boot off of a flash drive and go to GParted I see
/dev/sdb1/biosgrub, primary, 1mb, flags bios_grub
/dev/sdb2/ext4, primary, 25GB
/dev/sdb3/swap, primary, 4GB

Does that mean I should change /dev/sdb1/biosgrub to FAT32 and set the Boot and/or ESP flags?
I think it will be fine for that to be UEFI. But I find conflicting info online re EFI vs UEFI.
I'm not booting Windows and I'm not booting any old/legacy Linux installs. I'll install a recent Ubuntu such as Lubuntu 16, maybe I'll run a stable version of Ubuntu 18.

---

### Post by oldfred on 2018-10-29
The bios_grub partition is 1 or 2MB, but the ESP needs to be much larger. Windows default is 100MB, if drive is larger, I suggest 300 to 500MB. For may flash drive full installs I use the 100MB, but do not plan on lots of things going into the ESP.

I actually put both ESP & bios_grub as first two partitions on every drive. If ESP not directly used, I use it as a location for a copy of main boot drive which then could be booted if configured correctly.

---

### Post by webmanoffesto on 2018-10-30
So my SSD should have 
- bios_grub partition of 2MB (format, flag?)
- ESP partition of 300 MB (format, flag?)
- OS partition (format, flag?)
- / root (format, flag?)

/Home goes on 1TB spinning disk'
I'll probably install Lubuntu. Do you know how I specify during install that /Home goes on another drive?

Is that correct?

When I go to GParted on my main laptop I don't see either a bios_grub partition or an ESP partition. I see 
Partition: /dev/sda1, File System: ext4 Mount Point: root, Size: 19GB, Flags: boot
Partition: /dev/sda2, File System: ext4 Mount Point: /home, Size: 880GB, Flags: none
Partition: /dev/sda3, File System: linux-swap Mount Point: blank, Size: 31GB, Flags: none

---

### Post by oldfred on 2018-10-30
You do not really need the bios_grub. 
It is just an old habit of mine as I started with BIOS boot from gpt back in 2010 and then when Windows converted to UEFI in 2012, I started to add an ESP, even though I did not have an UEFI based system. Then in 2014 when I got the new system, I still put both on every drive just in case I wanted a BIOS boot.

And since 32GB is not a large drive, I would only use 100MB, FAT32 with boot & esp flags. Then / as ext4 will be the rest of the SSD.
Your /home  as ext4 can go on HDD and as large as you want, but maybe not all of drive. I typically have another ESP, / for test installs, and several other partitions.

More advanced is keeping /home inside /, but having data partition(s) and linking data back into /home so it looks & acts like all data is in /home, but is not. Standard desktops do not need /boot. The /boot is still used for default full drive LVM, but now does not have to be. Swap is now a file, so no partition required for it either.

But if a newer user the advantage if installing with separate /home is that it automatically gives you ownership & permissions and mounts /home in fstab. 
If you use a data partition, you have to do all that yourself, so best only after you have learned about Linux.

---

