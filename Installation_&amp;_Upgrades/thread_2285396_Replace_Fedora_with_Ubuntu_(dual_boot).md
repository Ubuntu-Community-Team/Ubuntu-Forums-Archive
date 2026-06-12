---
title: "Replace Fedora with Ubuntu (dual boot)"
date: 2015-07-05
forum: Installation &amp; Upgrades
---

### Post by Kntf on 2015-07-05
Hi,

I currently have a system installed with Windows 8 and Fedora. I've decided to go from Fedora to try Ubuntu for a change. I want to replace my Fedora installation with Ubuntu, but I don't want to touch the Windows partition. Can anyone guide me in the right direction as I'm afraid I will screw up

How can I replace Fedora with Ubuntu without screwing up?.

I have a EFI configured grub bootloader.

[http://i58.tinypic.com/10y1fd2.png](http://i58.tinypic.com/10y1fd2.png)

```
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectorsUnits: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 992444D1-A789-4F1C-A362-9C8EE7845D01


Device           Start          End   Size Type
/dev/sda1         2048       616447   300M Windows recovery environment
/dev/sda2       616448       821247   100M EFI System
/dev/sda3       821248      1083391   128M Microsoft reserved
/dev/sda4      1083392    853893119 406.7G Microsoft basic data
/dev/sda5    853893120    854917119   500M Microsoft basic data
/dev/sda6    854917120    976773119  58.1G Linux LVM




Disk /dev/mapper/fedora-root: 33.8 GiB, 36318478336 bytes, 70934528 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/fedora-swap: 7.8 GiB, 8338276352 bytes, 16285696 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/mapper/fedora-home: 16.5 GiB, 17729323008 bytes, 34627584 sectors
Units: sectors of 1 * 512 = 512 bytesa
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes



```

Everything is on the same disk obviously.

Thanks in advance!

---

### Post by wildmanne39 on 2015-07-05
Please use thumbnails or url's when posting images because many people have slow connections or a limit on bandwidth.
Thanks

---

### Post by Kntf on 2015-07-05
Sure, thanks for letting me know.

---

### Post by ajgreeny on 2015-07-05
You will certainly need to make use of the **"Something Else"** option, ie manual partitioning when you get to that point of the installation, but my uncertainty is how the ubuntu installer will deal with and see your current LVM Fedora install, or how you could keep LVM when installing Ubuntu.

As you will gather LVM is completely unknown to me, but as you presumably do understand how it works, having already got a system with it, it may simply be a case of choosing LVM in the process, and pointing the installer to use only /dev/sda6.

---

### Post by oldfred on 2015-07-05
The Ubuntu LVM install option is a full drive install, or it erases everything. Do not choose a LVM install unless you know how to manually configure it to only use one partition. But that defeats the main advantage of LVM which is one large space on a drive where you can create and move partitions around. You cannot boot Windows from LVM either.

And any major system change has risks. Make sure you have current backups of everything you want to preserve.

Best to just delete the LVM partition, make sure you have backed up any data in the Fedora install first that you want to keep.

       UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)


 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

