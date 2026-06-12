---
title: "Linux doesn't seem to detect my secondary HDD"
date: 2014-06-27
forum: Installation &amp; Upgrades
---

### Post by fredericobsr on 2014-06-27
I have windows on my SSD (32GB), that the boot and the windows (Windows 8.1 64 bits) uses, but I'd like to install linux in the HDD (1 TB), because the SSD is almost full, but I have been having problems.
First I created the linux partition (80 GB) on the windows partitioner, and left it unalocated, but when I ran the Linux live cd it shows [http://imgur.com/VHxHGYI](http://imgur.com/VHxHGYI) this and the same thing on GParted, and when I run ```
sudo gdisk -l /dev/sdb
``` it shows this [http://imgur.com/h0ikMgD](http://imgur.com/h0ikMgD), so what can I do, I want to install linux but my computer isn't helping.

EDIT: It also shows my partition as protected GPT partition.

---

### Post by Vladlenin5000 on 2014-06-27
> **fredericobsr said:**
> First I created the linux partition (80 GB) on the windows partitioner, and left it unalocated

This is your first problem. Whether or not it affects the rest I don't know yet. Let's wait for some experts.
What I can tell you right now is the quoted part of your post makes no sense at all. Creating a partition allocates the space by definition. Also by definition, any unallocated part of a drive is unpartitioned. You can't have both. Plus you CAN'T create Linux partitions in Windows.

I suspect the whole problem stems from whatever you used in Windows. Dynamic disks (or whatever they call that PITA), perhaps?

---

### Post by nerdtron on 2014-06-27
Go to windows and open up the disk partitioner. Post the layout of your hard drive here. I think your 1TB drive is formatted as what windows calls a "dynamic disk" which you can't use to install ubuntu on. The best way to do this is to format the 1TB partition and make it a "normal" drive.

---

### Post by grahammechanical on 2014-06-27
The first image shows that Linux/ubuntu has detected your second hard disk - sdb. but it has not been partitioned. It does not even have one partition taking up the whole disk. If you highlight/select sda the partioner should show that 80 GB unallocated space which I assume is what you did - re-size the Windows partitions to create 80 GB unallocated space.

What do you want to do with that 80 GB of space? Install Ubuntu into it? Then you need to turn it into a partition and direct the installer to install Ubuntu into it. What do you want to do with the second disk? Use it for data? Then you need to create at least one partition and then format it. If you want both Windows and Linux to access files on the second disk it should be formatted with a Windows format. If you format it with a Linux format (Ext4) then Windows will not be able to access the files on it.

If, on the other hand you want to put Ubuntu on the second disk, then I suggest that you disconnect the SSD so that the Ubuntu installer only sees the hard disk and then tell the installer to use the whole disk. It will create 2 partitions - 1 for Ubuntu and 1 for swap. You can later use the live session to shrink the Ubuntu partition to create unallocated space which can be used to create other partitions if this is what you want.

You can use the BIOS/UEFI to choose to boot into the SSD (Windows) or the HD (Ubuntu). If you boot into Ubuntu and run

```
sudo update-grub
sudo grub-install /dev/sdb
```

Then you will get a Grub boot menu that allows you to boot into Windows on the SSD.

Regards.

---

### Post by oldfred on 2014-06-28
Post this from live installer's terminal.

sudo parted -l

Install gdisk and post its version of partitions.

sudo apt-get install gdisk
       sudo gdisk -l /dev/sda
            sudo gdisk -l /dev/sdb

---

