---
title: "RAID issues, why won't this work?"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by Rax on 2006-05-01
I have 4 SATA 200GB drives hooked up.  Grub won't boot with raid5 so I set up each of the disks as follows:

- Primary #1 - 50MB - Physical Volume for raid
- Primary #2 - 200GB - Physical Volume for raid

Why can't I then create a Raid1 array with the 4x50mb partitions (1 active, 3 spares) and a Raid5 array with the 4x200gb partitions (3 active, 1 spare)?

---

### Post by supergrover on 2006-05-03
I have the same problem. I can't get this to work at all. Here is the system:

K8N-DL
2xOpteron 265
4x250GB SATA-II 

Using Ubuntu 5.10 X64

I have tried following several guides for setting up raid 0 or 1 and adapting it for RAID 5, but it never works. Also, if I do a straight install to one volume, the system does not boot. 

I also can't seem to get past this bug/quirk:
[https://launchpad.net/distros/ubuntu/+source/parted/+bug/22899](https://launchpad.net/distros/ubuntu/+source/parted/+bug/22899)

Any ideas or a pointer to a clear guide for setting this up? 

Ideally, I would like to have a small boot partition (RAID 1 on each drive?) and the rest of the space should be LVM + RAID 5. This system is strictly for running VMware Server (Beta) and act as a file server.

Thanks in advance.

Update:
I tried many times doing a plain install (non-raid) with 5.10 and Dapper beta... all no go. The system does NOT boot the OS after completing a sucessful install. After removing the CD/DVD and rebooting it just sits after POST. There isn't anything wrong with the HW, an install of Windows XP x64 boots and works perfectly. What step could I be missing? I have manually tried installing both GRUB and LILO and each time, the same result, no boot. If I can't get this working this morning, I'll be forced to just switch back to Windows XP x64 to run VMware and just move on. :( I really want to get this working.

---

### Post by jesta_ on 2006-06-03
I just had this problem with my Asus A8N-SLI Deluxe board with Ubuntu 6.06. The LiveCD install would finish and then after reboot it would hang after POST. I have 4 SATA drives and Ubuntu would detect the drive hooked up to the SATA3 motherboard connection as sda1. I fixed this by going into the BIOS, "Boot", "Hard Disk Drives" and moved "3rd SATA-M" to #1.

-jesta

---

### Post by therunnyman on 2006-06-03
This is a well-known and well documented bug.  About 300 people filed a variant, we all confirmed each others' bugs, but the devs won't do anything about it.

Near as I can tell Dapper mounts whatever SATA drives are plugged into your card first as sda and sdb, then it mounts the mobo SATA drives as sdc and sdd.  I'm pretty sure this is a problem in udev, and I think I know exactly which file, but I can't figure out how to rewrite it such that the drives mount properly.

therunnyman

PS HEY DEVS!  FIX THIS ALREADY!

---

### Post by jesta_ on 2006-06-05
I don't think it's a linux/ubuuntu specific problem. I just tried to install WinXP and it installed on the 3rd SATA disk, too. If anything, it seems an ASUS issue.

[edit]
n/m... I must be smoking crack

---

### Post by shane.gardner on 2006-12-15
I am having the same trouble (see: [http://www.ubuntuforums.org/showthread.php?t=319057)](http://www.ubuntuforums.org/showthread.php?t=319057)).  

I am going to try to take my drives out of RAID (since I am only using RAID to get my mobo bios to see the drive for booting purposes).  Then reinstall.

If that doesn't work I am going to try to install Bootloader on an IDE and then manual add a GRUB entry to boot to my SATA drive.

From what I am reading... solving this RAID dilemma for booting purposes in Linux is not so simple!

---

### Post by shane.gardner on 2006-12-17
I don't know if this will help at all, but I got my SATA/RAID drives to boot...

[http://www.ubuntuforums.com/showthread.php?t=320349](http://www.ubuntuforums.com/showthread.php?t=320349)

---

