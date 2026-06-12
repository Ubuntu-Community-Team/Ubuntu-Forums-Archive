---
title: "Launching Grub from External USB Drive"
date: 2011-04-01
forum: Installation &amp; Upgrades
---

### Post by 1234blizzard on 2011-04-01
Hi, I installed ubuntu 9.04 onto my external usb drive and then installed Windows 7 onto my internal drive. I then configured grub to be able to also launch Windows 7. 

Everything works except I have to turn on my external USB drive to launch grub and then get into my systems. Is there a way that I can launch grub without having to turn on my External USB drive? If the usb drive is not on, grub displays error 17.

Thanks!!

---

### Post by oldfred on 2011-04-01
9.04 was the last to use grub legacy by default.

You need to install grub's boot loader to the MBR of the external drive and install a windows or windows like boot loader to the MBR of the internal drive. Then set BIOS to boot the external first, it will then boot grub and if not found boot the windows boot loader in the internal.

From you 9.04 install grub to sdb if your external is sdb. Some system call an external sdf or some other higher letter.

sudo fdisk -l  # El not I
#confirm that it is sdb
grub-install /dev/sdb

Test that you can boot from sdb with change to BIOS or using one time boot key (f12 on mine).

The install lilo (or from a windows cd install window's boot loader)
Lilo works just like windows in the MBR as it looks for the partition with the boot flag (active partition in windows) and jumps to that partition to boot.

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR bootloader as we are booting windows not lilo.

---

### Post by 1234blizzard on 2011-04-01
When I typed in 

sudo fdisk -l # E1

I got this...

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x667dbdca

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       30394   244035584    7  HPFS/NTFS

Disk /dev/sdb: 504 MB, 504364544 bytes
4 heads, 8 sectors/track, 30783 cylinders
Units = cylinders of 32 * 512 = 16384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30784      492539+   6  FAT16

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004c011

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       13995   112414806   83  Linux
/dev/sdc2           13996       14593     4803435    5  Extended
/dev/sdc5           13996       14593     4803403+  82  Linux swap / Solaris


Then, I typed in

grub-install /dev/sdb

And it responded with 
/dev/sdc1 does not have any corresponding BIOS drive.

---

### Post by oldfred on 2011-04-01
It looks like you have plugged in a 500MB flash drive and it is sdb. That was why to run the fdisk command. You now see the Linux partitions are on sdc. You are running this from your install in sdc, not from a Cd or USB liveCD version.

You may also need sudo ( I still do not know when or not and just add it when ever I get an error).

sudo grub-install /dev/sdc

---

### Post by 1234blizzard on 2011-04-02
Thank you very much. My computer now launches without the need of the external hard drive. Thank You!!

---

### Post by oldfred on 2011-04-02
Glad it worked. Happy Ubuntu-ing.:)

---

