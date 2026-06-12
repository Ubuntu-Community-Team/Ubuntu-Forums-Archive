---
title: "Partitioning, again :)"
date: 2005-10-12
forum: Installation &amp; Upgrades
---

### Post by Pablo_Escobar on 2005-10-12
While waiting for Breezy release a big problem of mine came back to haunt me.

Last time I've installed Hoary (3 months back) I wanted to setup a seperate /home partition.
In the installer I've made "/" and swap partition, but when I wanted to make "/home" it borked some error. I wonder.
AFAIK You can only setup 4 primary partitions. Here is hom my SATA drive looks like:
These are my primary partitions:
sda1 - NTFS - (circa 6GB) WinXP (Yes, I still dual boot sometimes)
sda2 - EXT3 - "/" (circa 9 GB) Ubuntu
sda3 - SWAP - circa 1,2 GB

Then comes the extended partitions time:
sda5 - FAT32 - (circa 30GB)
sda6 - FAT32 - (circa 40GB)
sda7 - FAT32 - (circa 20GB)

My question is why can't I make another primary partition form my "/home" ?
Do I have to loose WinXP partition (I'm willing to do it ) to make a free slot for primary partition.

This problem has been tested for me on several installers (Fedora, Slackware, Ubuntu) and none of them could create it

Any thoughts would be appreciated :)

Posted it firstly in Warty section by mistake :???:

---

### Post by SilentCacophony on 2005-10-12
Hello. From what I know of harddrive partitions, the reason you can't create another primary partition, is that the extended partitions are actually logical partitions within the 4th primary 'extended' partition. Maybe a diagram will explain better:

```
sda1 - NTFS - (circa 6GB) WinXP (Yes, I still dual boot sometimes)
sda2 - EXT3 - "/" (circa 9 GB) Ubuntu
sda3 - SWAP - circa 1,2 GB
sda4 - EXTENDED - Containing the logical partitions:
   sda5 - FAT32 - (circa 30GB)
   sda6 - FAT32 - (circa 40GB)
   sda7 - FAT32 - (circa 20GB)
```

For example, my setup is similar:

```
brian@ubuntu:~$ sudo fdisk -l
Password:

Disk /dev/hda: 20.4 GB, 20493656064 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           2         312     2498107+   b  W95 FAT32
/dev/hda2             313         697     3092512+  83  Linux
/dev/hda3             698        1338     5148832+  83  Linux
/dev/hda4            1339        2491     9261472+   f  W95 Ext'd (LBA)
/dev/hda5            1339        1851     4120641   83  Linux
/dev/hda6            1852        2364     4120641   83  Linux
/dev/hda7            2365        2491     1020096   82  Linux swap / Solaris
```

Your best bet would be to use or make room for another logical partition for your /home, I think.

---

### Post by Pablo_Escobar on 2005-10-12
That's what I thought.

Thanks for confirming my speculations :)

I've got to do some partition moving :D

---

### Post by SilentCacophony on 2005-10-12
No problem. I don't expect there is any problem with using a logical partition for /home. I have my swap set as hda7, for instance.

---

