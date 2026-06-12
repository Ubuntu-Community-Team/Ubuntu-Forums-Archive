---
title: "fsck.ext4: unable to set superblock flags on /dev/nvme0n1p5"
date: 2021-05-24
forum: Installation &amp; Upgrades
---

### Post by hasanijaz on 2021-05-24
The laptop was hung up, so I forced a shutdown using the power key. After that it booted with errors. 

In the first attempt fsck fixed the issues but on the next boot I had similar errors and now I get **unable to set superblock flags**.
I have installed my root filesystem and have my home partition on an **NVME** device. And have a secondary hard disk. 
```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/nvme0n1: 111.81 GiB, 120034123776 bytes, 234441648 sectors
Disk model: HP SSD EX900 120GB                      
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2349e3d9

Device         Boot    Start       End   Sectors   Size Id Type
/dev/nvme0n1p1 *        2048   1269759   1267712   619M ef EFI (FAT-12/16/32)
/dev/nvme0n1p2       1271806 234440703 233168898 111.2G  5 Extended
/dev/nvme0n1p5       1271808  49270783  47998976  22.9G 83 Linux
/dev/nvme0n1p6      49272832 234440703 185167872  88.3G 83 Linux


Disk /dev/sda: 931.53 GiB, 1000204886016 bytes, 1953525168 sectors
Disk model: ST1000LM035-1RK1
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 6CBC3BD7-2FA3-4A13-9F0A-439C6AA249C5

Device          Start        End    Sectors   Size Type
/dev/sda1        2048 1750003711 1750001664 834.5G Linux filesystem
/dev/sda2  1750003712 1751273471    1269760   620M EFI System
/dev/sda3  1751273472 1823277055   72003584  34.3G Linux filesystem
/dev/sda4  1823277056 1953523711  130246656  62.1G Linux filesystem


```

I have tried everything in this: [https://ubuntuforums.org/showthread.php?t=2282368](https://ubuntuforums.org/showthread.php?t=2282368)
```
sudo fsck -yv /dev/nvme0n1p5
fsck from util-linux 2.34
e2fsck 1.45.5 (07-Jan-2020)
/dev/nvme0n1p5: recovering journal
Superblock needs_recovery flag is clear, but journal has data.
Run journal anyway? yes

fsck.ext4: unable to set superblock flags on /dev/nvme0n1p5


/dev/nvme0n1p5: ********** WARNING: Filesystem still has errors **********

```

```
sudo e2fsck -C0 -p -f -v /dev/nvme0n1p5
/dev/nvme0n1p5: recovering journal
/dev/nvme0n1p5: Superblock needs_recovery flag is clear, but journal has data.
/dev/nvme0n1p5: Run journal anyway

/dev/nvme0n1p5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)


```

Then this tutorial on repairing a broken superblock on Ext4: 
[https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](https://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)


```
sudo mke2fs -n /dev/nvme0n1p5
mke2fs 1.45.5 (07-Jan-2020)
/dev/nvme0n1p5 contains a ext4 file system
    last mounted on /media/ubuntu/f3c10efe-eda7-43fb-b7b2-90ffb2192fd2 on Sun May 23 18:53:43 2021
Proceed anyway? (y,N) y
Creating filesystem with 5999872 4k blocks and 1501440 inodes
Filesystem UUID: 3efb1657-3bf3-4b59-868e-aa54a5819769
Superblock backups stored on blocks: 
    32768, 98304, 163840, 229376, 294912, 819200, 884736, 1605632, 2654208, 
    4096000


```

I used the following command on each of the above blocks and rebooted every time :(:(:(
```
sudo e2fsck -b 32768 /dev/nvme0n1p5
```

No luck

I used **mkfs.ext4  **too but of no avail. Rebooted etc
this seemed promising: 


[https://ubuntuforums.org/showthread.php?t=1682038](https://ubuntuforums.org/showthread.php?t=1682038)
```
sudo debugfs -w /dev/nvme0n1p5
debugfs 1.45.5 (07-Jan-2020)
/dev/nvme0n1p5: Block bitmap checksum does not match bitmap while reading allocation bitmaps
debugfs:  clri <8>
clri: Filesystem not open
debugfs:  


```
But again of no avail


I just want to get things going. Its been three days, I have tried to erase the disk but gparted wont work. **dd** won't work. 
I have tried every option from the live cd to re install, but nothing is working. I have even tried to install another copy of ubuntu
on the other hdd /dev/sda but that won't go through. 

Please HELP!

---

### Post by hasanijaz on 2021-06-02
I tried to format it using a Windows Installer disk, but that didn't work out. So I just turned it in for a warranty. 

I

---

