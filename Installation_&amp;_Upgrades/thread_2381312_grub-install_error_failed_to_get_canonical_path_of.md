---
title: "grub-install: error: failed to get canonical path of `aufs'."
date: 2017-12-29
forum: Installation &amp; Upgrades
---

### Post by tezarin on 2017-12-29
Hi all,

I am ty install Ubuntu from a USB drive and after clicking on try Ubuntu, I can't seem to be able to install it. The most recent error is: grub-install: error: failed to get canonical path of `aufs'.

Here is the output for my filesystem:

```

ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Installing for i386-pc platform.
grub-install: error: failed to get canonical path of `aufs'.




ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x6eb2f17c


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x3918dc95

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1            2048 960878591 960876544 458.2G 83 Linux
/dev/sdb2       960880638 976771071  15890434   7.6G  5 Extended
/dev/sdb5       960880640 976771071  15890432   7.6G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.


Disk /dev/sdc: 3.6 GiB, 3868430336 bytes, 7555528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x001d45d5

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7555527 7553480  3.6G  c W95 FAT32 (LBA)

ubuntu@ubuntu:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
udev           devtmpfs  3.7G     0  3.7G   0% /dev
tmpfs          tmpfs     756M  9.6M  747M   2% /run
/dev/sdc1      vfat      3.6G  1.5G  2.2G  42% /cdrom
/dev/loop0     squashfs  1.5G  1.5G     0 100% /rofs
aufs           aufs      3.7G  131M  3.6G   4% /
tmpfs          tmpfs     3.7G  488K  3.7G   1% /dev/shm
tmpfs          tmpfs     5.0M  8.0K  5.0M   1% /run/lock
tmpfs          tmpfs     3.7G     0  3.7G   0% /sys/fs/cgroup
tmpfs          tmpfs     3.7G  892K  3.7G   1% /tmp
tmpfs          tmpfs     756M   80K  756M   1% /run/user/999
ubuntu@ubuntu:~$ 



```

I installed boot repair and then rebooted my machine, then it booted from USB and same exact issues as before. Can someone please help me fix this issue and successfully install Ubuntu?

Thanks

---

### Post by tezarin on 2017-12-29
More info:

sudo apt-get install -y boot-repair && boot-repair

ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 boot-repair : Depends: boot-sav but it is not going to be installed
 grub-pc : Depends: grub2-common (= 2.02~beta2-36ubuntu3.12) but it is not going to be installed
           Depends: grub-gfxpayload-lists but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

ubuntu@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 303 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up grub-pc (2.02~beta2-36ubuntu3.14) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)
ubuntu@ubuntu:~$ sudo apt-get install -y boot-repair && boot-repair
Reading package lists... Done
Building dependency tree       
Reading state information... Done
boot-repair is already the newest version (4ppa65).
0 upgraded, 0 newly installed, 0 to remove and 303 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
Setting up grub-pc (2.02~beta2-36ubuntu3.14) ...
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 grub-pc
E: Sub-process /usr/bin/dpkg returned an error code (1)


Can someone please help? I am really dead in the water now. Thanks

---

### Post by tezarin on 2017-12-29
Here's my fdisk output:

```


ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.4 GiB, 1532116992 bytes, 2992416 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda: 29.8 GiB, 32017047552 bytes, 62533296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x7f8d8f56


Disk /dev/sdb: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x3918dc95

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdb1            2048 960878591 960876544 458.2G 83 Linux
/dev/sdb2       960880638 976771071  15890434   7.6G  5 Extended
/dev/sdb5       960880640 976771071  15890432   7.6G 82 Linux swap / Solaris

Partition 2 does not start on physical sector boundary.


Disk /dev/sdc: 3.6 GiB, 3868430336 bytes, 7555528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x001d45d5

Device     Boot Start     End Sectors  Size Id Type
/dev/sdc1  *     2048 7555527 7553480  3.6G  c W95 FAT32 (LBA)



```

---

### Post by oldfred on 2017-12-29
What is sda, the 29.8GB drive. Do you have another flash drive plugged in or Intel SRT SSD, or MicroSD card?
That is confusing installer. Grub normally defaults to install to sda.

If Intel SRT, you will have to remove RAID meta-data. And make sure BIOS is in AHCI mode.

---

