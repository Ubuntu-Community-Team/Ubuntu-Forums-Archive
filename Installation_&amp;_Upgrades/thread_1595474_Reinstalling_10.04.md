---
title: "Reinstalling 10.04"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by welshmike on 2010-10-13
I have a dual boot XP/Ubuntu system. The Ubuntu system is 10.04 upgraded from 9.10.
I want to reinstall a clean 10.04.
It is not clear to me how I do this during the install process (from a CD) when the installation gets to the partitioning page.
How may I do this please?
(I don't want to lose the XP system as I need it for a couple of Windows only applications).

---

### Post by Rubi1200 on 2010-10-13
Please post the output of ```
sudo fdisk -l
``` from within Ubuntu. (lowercase L not 1)

Thanks.

---

### Post by welshmike on 2010-10-13
(I'm posting this from a PC other than the one I want to reinstall 10.04 on)
Since posting my message I foolishly tried to reinstall 10.04 by telling the install process to install systems side by side. The process started partitioning the hard drive and stalled at 50%. Now I'm not able to boot Ubuntu but can still boot XP.
I've booted from my 10.04 USB and here is the output you requested:
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x28f99123

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        7296    33005512    5  Extended
/dev/sda5            3188        7181    32081773+  83  Linux
/dev/sda6            7182        7296      923706   82  Linux swap / Solaris

Disk /dev/sdb: 2115 MB, 2115502080 bytes
66 heads, 62 sectors/track, 1009 cylinders
Units = cylinders of 4092 * 512 = 2095104 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f052b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1009     2064383    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

```

---

### Post by Rubi1200 on 2010-10-13
If you choose the side-by-side option it will shrink the Windows partition and put Ubuntu there. In my opinion, this is not a good way to do things as it might cause problems on the Windows side.

Anyway, I would suggest you run the installer from the LiveCD/USB and select manual partitioning when that point comes and tell it to install to sda5. Ubuntu will format the partition and then install.

Leave the swap partition on sda6 untouched.

GRUB will be installed as the bootloader and allow you to boot both Windows and Ubuntu.

---

### Post by welshmike on 2010-10-13
Let me thank you publicly for you help. Many many thanks. Installation completed successfully and I now have a dual boot XP/Ubuntu 10.04 system with a clean Ubuntu (as against an upgraded one).

---

### Post by Rubi1200 on 2010-10-13
You are more than welcome :)

Please mark this thread Solved using the Thread Tools near the top of the page.

Enjoy!

---

