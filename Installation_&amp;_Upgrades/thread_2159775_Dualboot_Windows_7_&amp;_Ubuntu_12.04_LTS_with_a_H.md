---
title: "Dualboot Windows 7 &amp; Ubuntu 12.04 LTS with a HDD for win and ssd for ubuntu"
date: 2013-07-04
forum: Installation &amp; Upgrades
---

### Post by thedual5s on 2013-07-04
Good day, 


     I have been trying to setup a dual boot system with windows 7 installed on a 1TB hard drive and ubuntu installed on a 120GB SSD. I have done alot of reading and have also come pretty far, but I am stuck. below is what I have done and some various info about my setup


Sata0 - 1TB HDD
Sata1 - CD/DVD Burner
Sata2 - 120 GB SSD
Motherboard: Asus 990FX
**UEFI**

1. Installed WIndows 7 on to the 1TB Drive, This is while in UEFI the SSD is set to Primary boot device. 
2. reboot and varify that the SSD is still primary boot device, it is not. EUFI won't allow me to make it primary, I'm guessing because nothing is on it so it recogognizes that. 
3. I go ahead and boot to the Ubuntu CD and install Ubuntu on the SSD with a 500MB /boot, a 32GB /swap and the rest as /. reboot
4. go into UEFI and put the SSD as primary boot device. no problem. reboot. 
5. machine boots right into Unbuntu with out the grub boot menu, no big deal, tried holding down shift while reboot, still no Grub boot menu. 
6. booted to live Ubuntu and installed boot repair, it ran without issue and gave me [http://paste.ubuntu.com/5843951/](http://paste.ubuntu.com/5843951/) as the trobleshooting file. I now get a GRUB boot menu and Ubuntu works fin, but when I try to use any of the 3 options refereing to windows, I get: Error: no such device: UUID (I can't remember the UUID at this moment but can grab it when I reboot.) 

the exact error is:
[I]
error: no such device: [/I]UUID[I]
error: file not found

press any key to continue....[/I]


This is where I am at. Any assistance would be greatly appricaited. Let me know if you need more information. Thanks for you help.

---

### Post by sudodus on 2013-07-04
Welcome to the Ubuntu Forums :-)

1. Did you install Windows 7 yourself? Then I suggest that you install it without UEFI (if you can set the BIOS in another mode, sometimes called CSM). This will make it much easier for you.

2. But if the computer came with Windows preinstalled in UEFI mode, you have no choice.

3. In UEFI mode: Shut off secure mode if possible, shut off fast boot if possible.

4. You need a gpt partition table (not the standard msdos one with mbr) for all drives with operating systems to be booted.

---

### Post by thedual5s on 2013-07-04
> **sudodus said:**
> Welcome to the Ubuntu Forums :-)

1. Did you install Windows 7 yourself? Then I suggest that you install it without UEFI (if you can set the BIOS in another mode, sometimes called CSM). This will make it much easier for you.

2. But if the computer came with Windows preinstalled in UEFI mode, you have no choice.

3. In UEFI mode: Shut off secure mode if possible, shut off fast boot if possible.

4. You need a gpt partition table (not the standard msdos one with mbr) for all drives with operating systems to be booted.


Thank you for the quick reply. I beleive that both boot partitioins are GPT. Secure mode and fast boot are both turned off. 

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2c66947

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048      976895      487424   83  Linux
/dev/sdb2          976896    63477759    31250432   82  Linux swap / Solaris
/dev/sdb3        63479806   234440703    85480449    5  Extended
/dev/sdb5        63479808   234440703    85480448   83  Linux

---

### Post by sudodus on 2013-07-04
1. Did you install Windows 7 yourself? Then I suggest that you install it without UEFI (if you can set the BIOS in another mode, sometimes called CSM). This will make it much easier for you. Unless, of course you want to learn howto manage UEFI,

2. /dev/sdb has an extended partition. This is a feature of msdos partition tables, so it is not gpt. It will not work in UEFI mode. You can create gpt with gparted, but you must select ***advanced*** for the partition table.

---

### Post by fantab on 2013-07-04
Your HDD has GPT but your SSD has 'msdos' partition table. You have to change this to GPT. Both OS must be installed in either UEFI or Legacy Bios. To Boot in UEFI you must have Ubuntu installed in UEFI mode.

Using Gparted Delete all the partitions on SSD and change the partition table to GPT. This can be done with Gparted -> Devices -> create Partition Table. GPT will be under advanced options.

After which create the first partition of about 300MB and format it with FAT32, create other partition you need then Reinstall ubuntu. If you have trouble booting windows then run Boot-Repair.

---

