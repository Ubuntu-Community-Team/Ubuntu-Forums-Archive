---
title: "Windows boot UEFI entry"
date: 2017-04-20
forum: Installation &amp; Upgrades
---

### Post by onemorepash on 2017-04-20
Hi all,

About a year ago I've gotten a work laptop with two disks: HDD (sda) and SSD (sdb) with Windows installed on the SSD.

Well, I thought, I install Ubuntu on the HDD and keep Windows on the SSD with UEFI boot menu. So I did but had some issues with Ubuntu UEFI boot. After some struggling (it was quite ugly, BTW, I spent several nights of my life for this), reading forums and playing around with BIOS options I managed to boot Ubuntu finally. So I used it for some time and thought that I could boot Windows, if I need it, anytime with UEFI boot menu.

But no. My UEFI boot menu just doesn't have Windows option:

```
user@laptop:~$ sudo efibootmgr -v                                                                                                                                       
BootCurrent: 0014                                                                                                                                                           
Timeout: 0 seconds                                                                                                                                                          
BootOrder: 0014,000A,000F,000B,0012,0013,0010,000C,000D,000E,0000,0001,0002,0003,0004,0005,0006,0007,0008,0009,0011                                                         
Boot0000  Startup Menu  FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)....ISPH                                                    
Boot0001  System Information    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                          
Boot0002  Bios Setup    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                                  
Boot0003  3rd Party Option ROM Management       FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                          
Boot0004  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                          
Boot0005  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                          
Boot0006  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                          
Boot0007  System Diagnostics    FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                          
Boot0008  Boot Menu     FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                                  
Boot0009  HP Recovery   FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH                                                  
Boot000A* ubuntu        HD(1,GPT,05f49f04-0eff-4b32-80d4-45ba170b9554,0x800,0xee000)/File(\EFI\ubuntu\shimx64.efi)....ISPH
Boot000B* SanDisk SD7TN3Q-256G-1006     PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)N.....YM....R,Y.....ISPH
Boot000C* HGST HTS725050A7E630 :        BBS(HD,HGST HTS725050A7E630 : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(1,0,0)......ISPH
Boot000D* SanDisk SD7TN3Q-256G-1006 :   BBS(HD,SanDisk SD7TN3Q-256G-1006 : ,0x400)/PciRoot(0x0)/Pci(0x17,0x0)/Sata(4,0,0)......ISPH
Boot000E* Intel Corporation: IBA CL Slot 00FE v0106     BBS(Network,Intel Corporation: IBA CL Slot 00FE v0106,0x0)/PciRoot(0x0)/Pci(0x1f,0x6)......ISPH
Boot000F  USB:          PciRoot(0x0)/Pci(0x14,0x0)N.....YM....R,Y.....ISPH
Boot0010  USB:          BBS(65535,,0x0)/PciRoot(0x0)/Pci(0x14,0x0)......ISPH
Boot0011  Network Boot  FvVol(a881d567-6cb0-4eee-8435-2e72d33e45b5)/FvFile(9d8243e8-8381-453d-aceb-c350ee7757ca)......ISPH
Boot0012* IPV4 Network - Intel(R) Ethernet Connection (H) I219-LM       PciRoot(0x0)/Pci(0x1f,0x6)/MAC(ec8eb591c961,0)/IPv4(0.0.0.0:0<->0.0.0.0:0,0,0)N.....YM....R,Y.....ISPH
Boot0013* IPV6 Network - Intel(R) Ethernet Connection (H) I219-LM       PciRoot(0x0)/Pci(0x1f,0x6)/MAC(ec8eb591c961,0)/IPv6([::]:<->[::]:,0,0)N.....YM....R,Y.....ISPH
Boot0014* rEFInd Boot Manager   HD(1,GPT,05f49f04-0eff-4b32-80d4-45ba170b9554,0x800,0xee000)/File(\EFI\refind\refind_x64.efi)
```

However I am sure my Windows partitions including the EFI one are there:

```
user@laptop:~$ sudo parted /dev/sdb
GNU Parted 3.2
Utilisation de /dev/sdb
Bievenue sur GNU Parted ! Tapez 'help' pour voir la liste des commandes.
(parted) print
Modèle: ATA SanDisk SD7TN3Q- (scsi)
Disque /dev/sdb : 256GB
Taille des secteurs (logiques/physiques): 512B/4096B
Table de partitions : msdos
Disk Flags: 

Numéro  Début   Fin     Taille  Type     Système de fichiers  Fanions
 1      1049kB  1076MB  1075MB  primary  ntfs                 démarrage
 2      1076MB  235GB   234GB   primary  ntfs
 3      235GB   254GB   18,5GB  primary  ntfs
 4      254GB   256GB   2147MB  primary  fat32

(parted) ^C

user@laptop:~$ sudo mount /dev/sdb1 /mnt/tmp/
user@laptop:~$ cd /mnt/tmp/
Boot/                      Recovery/                  $RECYCLE.BIN/              System Volume Information/ 
user@laptop:~$ cd /mnt/tmp/
user@laptop:~$ ls
Boot  bootmgr  BOOTNXT  BOOTSECT.BAK  bootsqm.dat  Recovery  $RECYCLE.BIN  SYSTEM  System Volume Information


```

I played around a bit with boot-repare, installed rEFInd, as you can see, but didn't find a way to restore Wndows boot entry in UEFI.

Not that I really need it today, and probably never will, but as it's a work laptop, you never know what your IT managers might decide tomorrow.

The question is how to fix this. I've heard about Windows repair disk but first it requires a working Windows machine with admin privileges to create it, second I am afraid to break my linux boot which is quite critical as I use this thing every day for work.

So if anyone have an idea of a plan to avoid too much of dangerous experimenting, I would appreciate it.


Regards,
Pavel

---

### Post by oldfred on 2017-04-20
With pre-installed Windows in UEFI mode the FAT32 partition or ESP - efi system partition is one of the first partition.
Some vendors put vendor utilities in a FAT32 partition at end of the 4 primary partition limit with MBR(msdos).

You have MBR partitioning.
So you must have BIOS boot of Windows. 
Windows only boots from MBR with BIOS.
Windows only boots with UEFI from gpt partitioned drives.

UEFI & BIOS are not compatible. Once you start booting in one mode, you cannot change. Or from grub menu you can only boot other systems installed in same boot mode. You can dual boot different systems only from UEFI boot menu.

I do not know what  a BIOS boot entry looks like in UEFI. But one of your entries is the BIOS boot of the system. 
It may be just 000B or Sandisk since that is main drive?

---

### Post by onemorepash on 2017-04-20
Hm&#8230; Do you mean that I just need to switch to old good BIOS mode and try to boot from the SDD drive? Sounds like a plan. I'll check this out tomorrow and will let know here.

---

### Post by oldfred on 2017-04-20
If you installed Ubuntu in UEFI mode, you can convert using Boot-Repair to BIOS boot even if a gpt drive.
You first have to add a 1 or 2MB unformatted partition with the bios_grub flag anywhere on gpt drive.
Then use Boot-Repair's advanced options to uninstall grub-efi-amd64 and install grub-pc(BIOS boot).

Be sure to install grub2's boot loader to Ubuntu drive probably sdb. You want to keep Windows boot loader on Windows drive.
And do not use auto fix in Boot-repair as that installs grub to all drives.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by onemorepash on 2017-04-21
Well, I managed to boot Windows in classic BIOS mode.

An only issue was that my HP BIOS is somewhat new and cumbersome so it was not really obvious how to choose BIOS mode. Finally I switched from "Legacy support disable and secure boot disable" to "Legacy support enable and secure boot disable" in Secure Boot Options and *also* chose legacy boot order in Boot Options. There are two different boot order lists: UEFI and Legacy, while Legacy is not active if "Legacy support disable" is chosen under the Secure Boot options.

So it basically resolves my issue, thanks a lot, Oldfred. I also appreciate the recommendation to switch Ubuntu to BIOS mode to simplify dual-boot though not sure I will do it, as I don't really need dual boot. The fact that I can boot Windows occasionally if I need it is just what I need.

Thank you.

--
Pavel

---

