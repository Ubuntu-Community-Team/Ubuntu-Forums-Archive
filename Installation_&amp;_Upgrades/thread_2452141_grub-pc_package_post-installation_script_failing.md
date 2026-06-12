---
title: "grub-pc package post-installation script failing"
date: 2020-10-17
forum: Installation &amp; Upgrades
---

### Post by jcpfuntner on 2020-10-17
I upgraded to Ubuntu 20.04.1 and am getting this error with some apt commands:

```
$ sudo apt autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up grub-pc (2.04-1ubuntu26.4) ...
dpkg: error processing package grub-pc (--configure):
 installed grub-pc package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ 

```

Can anyone suggest how to fix this?

---

### Post by oldfred on 2020-10-17
Is this a BIOS install? Or system before 2012 which probably is BIOS only?
Post this:
sudo fdisk -lu

---

### Post by jcpfuntner on 2020-10-17
I'm not sure what kind of install it is.  Output from the command:

```
Disk /dev/loop0: 9.7 MiB, 9510912 bytes, 18576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop2: 9.7 MiB, 9506816 bytes, 18568 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop3: 97.6 MiB, 101777408 bytes, 198784 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop4: 54.98 MiB, 57626624 bytes, 112552 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop5: 179.74 MiB, 188452864 bytes, 368072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop6: 354.59 MiB, 371798016 bytes, 726168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop7: 97.72 MiB, 102445056 bytes, 200088 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 1.84 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ST2000LM015-2E81
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: F09816FD-143C-46F8-BBC8-6A7F3FF8E3DC


Device     Start        End    Sectors  Size Type
/dev/sda1   2048 3907026943 3907024896  1.8T Linux filesystem




Disk /dev/sdb: 232.91 GiB, 250059350016 bytes, 488397168 sectors
Disk model: Samsung SSD 850 
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 51F831F5-159A-4802-81B1-6F892D442740


Device         Start       End   Sectors   Size Type
/dev/sdb1       2048      4095      2048     1M BIOS boot
/dev/sdb2       4096 480006143 480002048 228.9G Linux filesystem
/dev/sdb3  480006144 488394751   8388608     4G Linux swap




Disk /dev/loop8: 55.33 MiB, 58007552 bytes, 113296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop9: 179.74 MiB, 188452864 bytes, 368072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop10: 355.41 MiB, 372662272 bytes, 727856 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```

---

### Post by oldfred on 2020-10-17
Grub defaults to installing to sda.
Your drives are gpt and you have the bios_grub partition on sdb for BIOS boot.
But if grub tries to install to sda, it will fail as sda has no bios_grub partition.

You can try adding a 1MB unformatted partition to sda with bios_grub flag if using gparted.
You may be able to use Boot-Repair's advanced mode and full reinstall of grub, but select sdb as install drive. Default repair may not suggest that.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If those suggestions do not work, post the link to the full Summary report from Boot-Repair (not the report itself).

---

