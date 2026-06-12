---
title: "GRUB Error"
date: 2010-07-05
forum: Installation &amp; Upgrades
---

### Post by pgs3223 on 2010-07-05
I have a Dell Inspiron laptop which was set up to dual boot windows Vista and Ubuntu 10.04.
   
  I created a live USB image for Ubuntu 10.04 using Unet bootin and rebooted from from this to install Ubuntu on an SD card.
   
  When I remove the SD card and reboot the laptop I no longer get the GRUB loader menu, instead I get the [FONT=&quot]“[/FONT]GRUB error[FONT=&quot]”[/FONT] message.
   
  I can not now boot into Windows Vista or Ubuntu!
   
  Obviously I have caused a GRUB error.
   
  I have rebooted using the USB live image and run fdisk –l and blkid, the outputs are listed below.
   
  Can anybody tell me how I can restore the GRUB loader menu back please so that I can access Ubuntu or Vista?
   
  fdisk -l
   
  Disk /dev/sda: 80.0 GB, 80026361856 bytes
  255 heads, 63 sectors/track, 9729 cylinders
  Units = cylinders of 16065 * 512 = 8225280 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0x28000000
     Device Boot      Start         End      Blocks   Id  System
  /dev/sda1               1          11       88326   de  Dell Utility
  /dev/sda2              12        1317    10485760    7  HPFS/NTFS
  /dev/sda3   *        1317        7357    48515184    7  HPFS/NTFS
  /dev/sda4            7358        9730    19054499    f  W95 Ext'd (LBA)
  /dev/sda5            9469        9730     2096128   dd  Unknown
  /dev/sda6            7358        9374    16201521   83  Linux
  /dev/sda7            9375        9468      755023+  82  Linux swap / Solaris
  
  Partition table entries are not in disk order
  Disk /dev/sdb: 2004 MB, 2004877312 bytes
  129 heads, 32 sectors/track, 948 cylinders
  Units = cylinders of 4128 * 512 = 2113536 bytes
  Sector size (logical/physical): 512 bytes / 512 bytes
  I/O size (minimum/optimal): 512 bytes / 512 bytes
  Disk identifier: 0xc3072e18
     Device Boot      Start         End      Blocks   Id  System
  /dev/sdb1   *           1         949     1957872    6  FAT16
  Partition 1 has different physical/logical endings:
       phys=(956, 128, 32) logical=(948, 75, 32)
  
  blkid
  
  /dev/loop0: TYPE="squashfs" 
  /dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D7-031B" TYPE="vfat" 
  /dev/sda2: LABEL="RECOVERY" UUID="6AE687FFE687CA31" TYPE="ntfs" 
  /dev/sda3: LABEL="OS" UUID="50EA8B50EA8B3170" TYPE="ntfs" 
  /dev/sda5: LABEL="MEDIADIRECT" UUID="1C8F-AF23" TYPE="vfat" 
  /dev/sda6: UUID="ffb33961-3fdd-4ee4-b36a-e3933a8758df" TYPE="ext4" 
  /dev/sda7: UUID="2a7b911f-ab7c-4a27-81cf-39c3dc67a59f" TYPE="swap" 
  /dev/sdb1: SEC_TYPE="msdos" UUID="9820-96C8" TYPE="vfat" 
  /dev/sdc1: UUID="4BB4-B907" TYPE="vfat"

---

### Post by darkod on 2010-07-05
From live mode it should be:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

Installing it on the SD card made grub2 go to the MBR but it can't work without the card now. The above commands will again install grub2 from your hdd installation to the MBR.

You should note that in this case you probably don't have grub2 on the SD card so you can't use it to boot any computer if that's what you planned.

---

### Post by pgs3223 on 2010-07-05
Thank you yet again Darko, if we ever meet I will buy you several beers!

I haven't had chance to try your suggestion yet but I have no doupt that you are right.

Your assumption about booting into Ubuntu from te SD card is also correct.

Can you advise me how to sort that out (I would select the SD card at Bios level as the PC boots).

Regards

pgs3223

---

### Post by Pumalite on 2010-07-05
You might find it useful looking at this too:
[http://ubuntuforums.org/showthread.php?t=1330183](http://ubuntuforums.org/showthread.php?t=1330183)

---

### Post by darkod on 2010-07-05
> **pgs3223 said:**
> Thank you yet again Darko, if we ever meet I will buy you several beers!

I haven't had chance to try your suggestion yet but I have no doupt that you are right.

Your assumption about booting into Ubuntu from te SD card is also correct.

Can you advise me how to sort that out (I would select the SD card at Bios level as the PC boots).

Regards

pgs3223

Just plug the card in but don't boot your hdd ubuntu, boot again in live mode. With fdisk check what is the Linux partition on the card and the card device name. Lets say the card device name is /dev/sdc and the Linux partition is /dev/sdc1.

In that case, to install grub2 onto the MBR of the card from live mode:

sudo mount /dev/sdc1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdc

---

