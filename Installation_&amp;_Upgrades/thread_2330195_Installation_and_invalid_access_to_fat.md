---
title: "Installation and invalid access to fat"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by marco139 on 2016-07-09
I tried to install ubuntu on my hp laptop. The installation stopped when it arrived at "Searching for other os". In particular the error was the following:
ubuntu kernel: [some numbers] FAT - fs(sda1): error invalid access to FAT
same message with different numbers
ubuntu ubiquity: find ... Input/output error

My first partition is a 400MB unallocated partition which I cannot merge with my unallocated space. 
I then created a new volume and tried to install ubuntu again. In that case, the sda mention in the kernel message was sda2

[IMG]https://s32.postimg.org/ixda1z4th/Capture.png[/IMG]

---

### Post by ubfan1 on 2016-07-09
Is Windows installed in UEFI mode?  If so, your disk partitioning is gpt, which is good, and you can just create any needed partitions for Ubuntu in the unallocated space.  If not, your disk may be using legacy partitioning, and that has a limit of four primary partitions, which you already have.  In that case, one next to the free space would need to be backed up, deleted, and a new "extended" partition created, in which you can create as many logical partitions as needed (one to hold the files backed up off D).   Now the error may be a problem in the EFI partition.  Run chkdsk on that a few times until there are no errors.

---

### Post by grahammechanical on 2016-07-09
What version of Windows? If it is Windows 8/10 then you will need to turn fast start up off. Hibernation is used to give Windows a fast start up but Linux cannot read any Windows partitions when Windows is in hibernation.

Try running the live session and load GParted. It is a partitioner. Do not do any partitioning. Just use it to find out what it sees in regards to the partitions.

Regards.

---

### Post by marco139 on 2016-07-09
I cannot use chkdsk on the efi partition.
I have windows 10 (updated from windows 8) and my fast boot is disabled.
I explain my problem better:
1) I tried to install ubuntu
2) There was an error: ubuntu kernel: [some numbers] FAT - fs(sda1): error invalid access to FAT
3) my sda1 was a 400Mb unallocated partition
4) I created a new volume using that space (The partition is called proof)
5) I tried to install ubuntu again
6) But now the problem was with sda2, which is the efi partition

It seems that I cannot use Gparted: the bios says "Selected boot image did not authenticate"

---

### Post by yancek on 2016-07-09
You have an EFI partition which means your windows system is using EFI and that you must both boot and install Ubuntu EFI.  Take a look at the Ubuntu documentation page below for an explanation.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

