---
title: "[SOLVED] Dual boot WINXP &amp;amp; Intrepid"
date: 2008-11-19
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-11-19
I have to have WinXP and do not want to use VirtualBox. Too many configuration issues and I only need it to work. I deleted Vbox and the XP installation and re-installed XP to a different drive.

I want to be able to dual boot from grub to WinXP or Intrepid with Intrepid as primary system.

I can work with grub for multiple Linux booting from several hard drives but have forgotten how to make it dual boot with XP. I will only be using XP and Ubuntu on separate drives.

Here is my system info:

> /dev/sda1: UUID="32dd3252-53b9-4647-b538-95793e7a55e2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="d81a0c0e-1b88-40fb-abed-2c9b15d0db6f" 
/dev/sdc1: UUID="30F70D6E790F4174" LABEL="Backups" TYPE="ntfs" 
/dev/sdd1: UUID="0708B48C6D9FA565" TYPE="ntfs" 
/dev/sdb3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdf1: SEC_TYPE="msdos" UUID="48F4-EAEE" TYPE="vfat" 
/dev/sde1: SEC_TYPE="msdos" UUID="48F4-EAEE" TYPE="vfat" 
/dev/sdd5: TYPE="swap" UUID="bf5881cf-1674-4f8e-a1b7-96083c9f0dd2" 
/dev/sdg1: UUID="48F4-EAEE" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdd2: UUID="1306a0e0-da49-4c2a-bc75-87a7c682aba3" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdh1: UUID="48EA-8696" TYPE="vfat" SEC_TYPE="msdos" 
/dev/sdi1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 
/dev/sdb5: TYPE="swap" UUID="4e1e2438-4522-4134-95c5-af5de6d4b796" 
/dev/sdc3: UUID="4f92449d-38a5-4453-b22e-9e3785987a02" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdc4: TYPE="swap" UUID="67e9932c-9bf7-4186-b147-0b534ed4080f" 
/dev/sdc5: TYPE="swap" UUID="4e1e2438-4522-4134-95c5-af5de6d4b796" 
/dev/sdb1: UUID="11b438ec-1bea-406f-b164-288e27296f3b" TYPE="ext2"Ubuntu is on sda and XP on sdd.[/quote]

Current "menu.lst" is:

> title        Ubuntu 8.10, kernel 2.6.27-7-generic
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
uuid        32dd3252-53b9-4647-b538-95793e7a55e2
kernel        /boot/memtest86+.bin
quietI have tried several Window options for booting but am getting errors for boot loader at best.

I have tried using "hd3" as the XP designation. It is actually the 1st drive in bios order.

> Hard drive physical order in BIOS:
IDE Channel 0 Master = Hitachi 250Gib WinXP NTFS (PATA)
IDE Channel 0 Slave  = ------
IDE Channel 2 Master = WD 160Gib Ubuntu 8.10 (SATA)
IDE Channel 2 Slave  = WD 40Gib No OS ntfs (SATA adapter)
IDE Channel 3 Master = Maxtor 160Gib ext2 (SATA)
IDE Channel 3 Slave  = CD/DVD (SATA)

Read from GParted:
/dev/sda = IDE Channel 2 Master = WD 160Gib Ubuntu 8.10 (SATA)
/dev/sdb = IDE Channel 3 Master = Maxtor 160Gib Kubuntu 8.10 (SATA)
/dev/sdc = IDE Channel 2 Slave  = WD 40Gib No OS ntfs (SATA adapter)
/dev/sdd = IDE Channel 0 Master = Hitachi 250Gib No OS format ext3 (PATA)> sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19457   156288321   83  Linux

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b230d97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081    7  HPFS/NTFS

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00009db3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       30401   244196001    7  HPFS/NTFS

Disk /dev/sde: 999 MB, 999816704 bytes
255 heads, 63 sectors/track, 121 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03910391

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         121      971901    b  W95 FAT32

Disk /dev/sdf: 4043 MB, 4043309056 bytes
255 heads, 63 sectors/track, 491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x04dd5721

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *           1         492     3948512+   b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 38)

Disk /dev/sdh: 1010 MB, 1010826752 bytes
32 heads, 61 sectors/track, 1011 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   ?      398636      983425   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdh2   ?       86419     1078237   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdh3   ?      957932     1949749   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdh4   ?     1478321     1478349       27749+   d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(1478320, 8, 25)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1478348, 22, 13)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk orderI have used Super Grub Disk to no avail. I may need to restore MBR to the NTFS/WinXP drive?

Could I use UUID to boot XP?

Any suggestions or more info needed?

---

### Post by markg48 on 2008-11-19
wubi install would have been easier

but any way you could create your partiton and install whatever os you like
and use neo smart easy bcd boot loader to point to these partitons u need to be in windows to
cofigure it though 
[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by 73ckn797 on 2008-11-19
I earlier had dual boot without wubi so I know it can be accomplished. I just forgot how.

---

### Post by markg48 on 2008-11-19
if you lazy like me you could create the partition on windows with whateva part program u use then get unetboot which lets you install linux to partition from within windows [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

then run easy bcd and point to the partition then reboot and u will have it on the boot loader

---

### Post by caljohnsmith on 2008-11-19
You might be able to use the "uuid" syntax in your menu.lst to boot Windows if you want to, but I think it would be simpler to just use the usual (hdX,Y) notation; I prefer the (hdX,Y) notation for Windows, because it is important to know whether Windows is on the first boot drive (hd0) or on a different drive. If Windows is on a different drive than (hd0), you have to use Grub's mapping technique to boot it properly; if you just have a "uuid" line to specify Windows drive/partition, then you don't know immediately whether mapping is necessary. 

Since you mentioned that you are booting your Windows sdd drive on start up, then your entry in Grub would simply be:
```
title Windows XP
root (hd0,0)
chainloader +1
```
Give that a shot and let me know how it goes, or if it doesn't work, let me know exactly what happens when you select it from the Grub menu. :)

---

### Post by 73ckn797 on 2008-11-19
> **caljohnsmith said:**
> You might be able to use the "uuid" syntax in your menu.lst to boot Windows if you want to, but I think it would be simpler to just use the usual (hdX,Y) notation; I prefer the (hdX,Y) notation for Windows, because it is important to know whether Windows is on the first boot drive (hd0) or on a different drive. If Windows is on a different drive than (hd0), you have to use Grub's mapping technique to boot it properly; if you just have a "uuid" line to specify Windows drive/partition, then you don't know immediately whether mapping is necessary. 

Since you mentioned that you are booting your Windows sdd drive on start up, then your entry in Grub would simply be:
```
title Windows XP
root (hd0,0)
chainloader +1
```Give that a shot and let me know how it goes, or if it doesn't work, let me know exactly what happens when you select it from the Grub menu. :)

I will check it when I get back home. I am on the road and checking in as I go along. Your input is always appreciated and I will follow-up later.

---

### Post by 73ckn797 on 2008-11-19
> **caljohnsmith said:**
> You might be able to use the "uuid" syntax in your menu.lst to boot Windows if you want to, but I think it would be simpler to just use the usual (hdX,Y) notation; I prefer the (hdX,Y) notation for Windows, because it is important to know whether Windows is on the first boot drive (hd0) or on a different drive. If Windows is on a different drive than (hd0), you have to use Grub's mapping technique to boot it properly; if you just have a "uuid" line to specify Windows drive/partition, then you don't know immediately whether mapping is necessary. 

Since you mentioned that you are booting your Windows sdd drive on start up, then your entry in Grub would simply be:
```
title Windows XP
root (hd0,0)
chainloader +1
```Give that a shot and let me know how it goes, or if it doesn't work, let me know exactly what happens when you select it from the Grub menu. :)


Back at you.

That did the trick my friend! I was not too far off in my feeble attempt to get things working. I had too much stuff included, trying to work from other info.

Who do I send the check to?

---

### Post by caljohnsmith on 2008-11-19
> **73ckn797 said:**
> Back at you.

That did the trick my friend! I was not too far off in my feeble attempt to get things working. I had too much stuff included, trying to work from other info.

Who do I send the check to?
Glad it worked, no need for a check; cheers and have fun with your OSes. :)

---

### Post by 73ckn797 on 2008-11-19
Ubuntu is for the fun and casual use. XP is because there are several work related necessities. I can live with that.

---

