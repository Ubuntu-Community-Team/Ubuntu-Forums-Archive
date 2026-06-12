---
title: "As if nothing happened"
date: 2012-06-30
forum: Installation &amp; Upgrades
---

### Post by aryzing on 2012-06-30
Hi All,
I have just run through what appeared to be a successful installation, with absolutely no errors. However, as soon as the PC restarted after the installation was completed, it booted straight into Win7 without any OS selection prompt screen or anything. There are no new screens between the moment I hit the power on button and the moment I see the Win7 logo... 

Any help will be much appreciated!

I have a laptop: ASUS 1215B, AMD-E350 processor, 8GB ram

---

### Post by darkod on 2012-06-30
Check if you have linux partitions on the disk.

Boot into live mode with the cd and in terminal try:
```
sudo fdisk -l
sudo parted /dev/sda print
```

Maybe just the grub2 bootloader didn't install. If that is the case, you can add only grub2, no need for full reinstall.

---

### Post by aryzing on 2012-06-30
Hi, the output of the commands you suggested are:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00098104

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848   582651358   291222255+   7  HPFS/NTFS/exFAT
/dev/sda3       582651902   625141759    21244929    5  Extended
/dev/sda5       609193984   625141759     7973888   82  Linux swap / Solaris
/dev/sda6       582651904   609193983    13271040   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4007 MB, 4007657472 bytes
255 heads, 63 sectors/track, 487 cylinders, total 7827456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcad4ebea

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           0           0           0    0  Empty
/dev/sdb4              63     7827455     3913696+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST9320325AS (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  106MB  105MB   primary   ntfs            boot
 2      106MB   298GB  298GB   primary   ntfs
 3      298GB   320GB  21.8GB  extended
 6      298GB   312GB  13.6GB  logical   ext4
 5      312GB   320GB  8165MB  logical   linux-swap(v1)

```

Thanks for your help!

---

### Post by darkod on 2012-06-30
OK, the linux partitions are there.

Again from live mode in terminal, try this:
```
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

Restart without the cd and see if it helped. If not, there is a longer procedure to run, this is the shorter version first.

---

### Post by aryzing on 2012-06-30
Restarting now, incase you are interested, the output from the commands you suggested was:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
/usr/sbin/grub-setup: warn: Sector 48 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

```

Thanks!

---

### Post by aryzing on 2012-06-30
All is great! Thanks a lot for your help and support. I finally get the GRUB screen and I can choose OS.

Thank you very much for your quick replies at this time of night!

---

### Post by darkod on 2012-06-30
Ah, the Flexnet message. It probably won't work.

You might need to use the boot-repair. You can do it from live mode too. Full instructions are here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I am not sure if the recommended repair can help, try that first.

If the recommended repair doesn't work, try it again but in the Advanced options, in the Grub options tab select the check box Reset extra space after MBR. If you look carefully in the instructions, in the screenshots about the advanced options, it mentions it solves the Flexnet error.

EDIT: Oops, it did work. Great. Didn't know simple grub2 reinstall can solve the Flexnet too. Enjoy your ubuntu now.

---

### Post by drs305 on 2012-06-30
> **darkod said:**
> EDIT: Oops, it did work. Great. Didn't know simple grub2 reinstall can solve the Flexnet too. Enjoy your ubuntu now.

Grub version 1.99 takes the 'Flexnet' problems into account. When it finds something written in the area to which it normally writes it adapts and records the information elsewhere.

+1 to enjoying Ubuntu.

---

### Post by aryzing on 2012-07-01
Thanks!

---

