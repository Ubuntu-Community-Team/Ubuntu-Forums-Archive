---
title: "GParted and deleting existing partitions"
date: 2022-02-02
forum: Installation &amp; Upgrades
---

### Post by username2758 on 2022-02-02
Hi,

A simple question just to make sure I am not doing it wrong.

I know it's kind of a mess but currently I have 4 operating systems and what seems to be a total of 8 partitions on this hard drive, and I intend to delete 3 out of the 4 existing operating systems partitions (Microsoft Windows partitions and ext4 partitions).

So based on the attached screenshot of my GParted below, can I safely delete sda1, sda2, sda3, sda4, sda5 and sda7? I want to keep sda6 (Ubuntu) and sda8 (data partition) and still be able to boot into Ubuntu. Will this procedure break GRUB?

I don't know I've never deleted Windows partitions manually before.

Thanks!

---

### Post by p2bc on 2022-02-02
So I would try first "lsblk", like list command "ls" to display what is a folder, but this is for block "blk" devices.

You should get something like:
```

sda      8:0    0 119.2G  0 disk 
&#9500;&#9472;sda1   8:1    0   512M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9492;&#9472;sda5   8:5    0 118.8G  0 part /
sdb      8:16   0 931.5G  0 disk 
&#9500;&#9472;sdb1   8:17   0   731M  0 part 
&#9500;&#9472;sdb2   8:18   0     1K  0 part 
&#9492;&#9472;sdb5   8:21   0 930.8G  0 part /home

```

So in this case you sda5 is mapped to my root folder, and sda1 is mapped to my boot folder.
Where as none of my sdb partitions are not mounted or mapped to any other part. It is just dangling out there unresolved.

My point is you will see all partitions and where there are pointing. So is in your case, if sda1, sda2, sda3... are just dangling out there then you OS don't need them to function.
Just a way to double check.

---

### Post by grahammechanical on 2022-02-02
If you delete sda1 you will break Grub because sda1 is the efi boot partition. It contains Grub boot files as well as the Windows boot files. With Guid Partition Table (GPT) drives there has to be an efi boot partition to contain the boot files for the OS. It is FAT32 so that Windows boot files can be loaded from it as was well as Linux boot files. If you are sure that you no longer need Windows then you can delete sda2, sda3, sda4, sda5 & sda7.

I would do it one partition at a time and test if Ubuntu still loads. I would start with sda7 and expand sda6 into the unallocated space. GParted takes a long time doing its stuff and stacking up a list of delete, move & resize actions can take what seems to be a very long time. I get nervous waiting. So I like to do the changes one at a time and assure myself that I still have a working OS.

The Windows boot files will still be in the efi boot partition. I think that you can remove them by going into the UEFI settings utility but I have next to no experience of doing that.

Regards

---

### Post by username2758 on 2022-02-02
@**p2bc**, 

I attached a screenshot of lsblk here.

> **grahammechanical said:**
> If you delete sda1 you will break Grub because sda1 is the efi boot partition. It contains Grub boot files as well as the Windows boot files. With Guid Partition Table (GPT) drives there has to be an efi boot partition to contain the boot files for the OS. It is FAT32 so that Windows boot files can be loaded from it as was well as Linux boot files. If you are sure that you no longer need Windows then you can delete sda2, sda3, sda4, sda5 & sda7.

I would do it one partition at a time and test if Ubuntu still loads. I would start with sda7 and expand sda6 into the unallocated space. GParted takes a long time doing its stuff and stacking up a list of delete, move & resize actions can take what seems to be a very long time. I get nervous waiting. So I like to do the changes one at a time and assure myself that I still have a working OS.

The Windows boot files will still be in the efi boot partition. I think that you can remove them by going into the UEFI settings utility but I have next to no experience of doing that.

Regards

Thanks for the info! 

I want to delete as many partitions as possible and keep only Ubuntu (sda6) and data partition (sda8), therefore keeping sda1, sda6 and sd8. 

Also, is it possible to expand the data partition? If so, what should I do in order to be able to do that?

---

### Post by yancek on 2022-02-03
Since you have an EFI system, you need to make sure Ubuntu is set to first boot priority in your BIOS firmware.  How to do this varies with different computer manufacturers so you''ll have to investigate that. As pointed out above, you can't delete the EFI partition and have Ubuntu boot but after you have finished with your changes, you can delete the windows and other boot files for the other Linux systems from the EFI partition. 

After deleting the partitions you want to delete, you can expand your data partition.  I would suggest you post back after deleting with an image of your system from GParted to get advice.

---

### Post by tea for one on 2022-02-03
It's a bit confusing from your two screenshots.

You have two disks on this PC?

Post no. 1 shows sda1 as ESP
Post no. 4 shows nvme0n1p1 as boot/efi

I think that you need to let us know what is installed on the nvme drive?

How many systems do you intend to end up with?

---

### Post by username2758 on 2022-02-03
> **yancek said:**
> Since you have an EFI system, you need to make sure Ubuntu is set to first boot priority in your BIOS firmware.  How to do this varies with different computer manufacturers so you''ll have to investigate that. As pointed out above, you can't delete the EFI partition and have Ubuntu boot but after you have finished with your changes, you can delete the windows and other boot files for the other Linux systems from the EFI partition. 

After deleting the partitions you want to delete, you can expand your data partition.  I would suggest you post back after deleting with an image of your system from GParted to get advice.

Yes, so it is possible to expand my data partition (sda8) after deleting other partitions on the same hard drive. But since I have like 8 partitions on this hard drive, isn't there a proper way to do this because the data partition is the last partition on the hard drive (sda8)? I remember I tried to do this once (delete and expand partitions), and I think I ended up with multiple unallocated spaces in between existing partitions, and I couldn't resize the target partitions I wanted which were to either the beginning or end of the hard drive, or something like that I guess (sorry I'm not a native English speaker and it's difficult to explain some things sometimes).

> **tea for one said:**
> It's a bit confusing from your two screenshots.

You have two disks on this PC?

Post no. 1 shows sda1 as ESP
Post no. 4 shows nvme0n1p1 as boot/efi

I think that you need to let us know what is installed on the nvme drive?

How many systems do you intend to end up with?

Yes I have two disks on this PC: one NVMe and one SATA.

I used to have all operating systems on the SATA disk because I hadn't purchased an NVMe SSD. Now that I finally bought an NVME SSD as a primary disk, the SATA disk has become my secondary disk and I intend to use it mainly as a data disk. But I intend to keep at least one operating system on this secondary disk for testing purposes, which will be Ubuntu (sda6).

---

### Post by tea for one on 2022-02-03
Deactivate, isolate or physically remove your primary nvme drive.
Ensure that you have a back up of your data partition from sda
Ensure that you have a back up of your personal data within Ubuntu on sda.

Use Gparted in a live session to remove the redundant partitions from your sata disk.
Retain the EFI partition on this disk.

Does the disk still boot?

---

### Post by ajgreeny on 2022-02-03
It will also be useful to know which of the Linux systems on the machine is managing grub, and I'm assuming you have more than one though it's not easy to know exactly what is present in all those ext4 partitions.

Which was the most recent Linux OS installed?
That will be the one which is managing grub and if you delete that OS partition you may find you have problems booting.

Although you do not currently have a boot problem, see **Boot-Repair** in my signature below and follow the instructions there to run just the Boot-Info-Script.	 
***Do not run the default repair just yet*** but simply copy back here the pastebin link you get which will show us a lot more about your system and my help us more.

---

### Post by username2758 on 2022-02-04
**@tea for one**

Yes, thanks for the advice! I will post the results later.

> **ajgreeny said:**
> It will also be useful to know which of the Linux systems on the machine is managing grub, and I'm assuming you have more than one though it's not easy to know exactly what is present in all those ext4 partitions.

Which was the most recent Linux OS installed?
That will be the one which is managing grub and if you delete that OS partition you may find you have problems booting.

Although you do not currently have a boot problem, see **Boot-Repair** in my signature below and follow the instructions there to run just the Boot-Info-Script.     
***Do not run the default repair just yet*** but simply copy back here the pastebin link you get which will show us a lot more about your system and my help us more.

I think it's Ubuntu managing GRUB on this SATA drive because it was the last operating system installed.

Do I still need to retain the EFI partition (sda1) if I am not going to use Windows anymore? Or it's best just to keep sda1 to make sure Ubuntu will boot normally after partition deletions?

---

### Post by tea for one on 2022-02-04
> **username2758 said:**
> 
I think it's Ubuntu managing GRUB on this SATA drive because it was the last operating system installed.

Do I still need to retain the EFI partition (sda1) if I am not going to use Windows anymore? Or it's best just to keep sda1 to make sure Ubuntu will boot normally after partition deletions?

Yes, you will need the EFI partition (sda1), assuming Ubuntu is installed in UEFI mode (which it should be)
When you have two drives each containing an OS, an EFI partition on each drive is highly desirable because each drive can be booted [COLOR="#0000FF"]independently[/COLOR].

You can double-check the installation mode by booting into Ubuntu on sda, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```

---

### Post by MAFoElffen on 2022-02-04
I would use boot-info and post the link to the pastebin results, to show what is installed, where, and where boot files are pointing to. That would also show the EFI files, and what is set in the EFI boot order. Then do a photo o the boot order (how it is set) in your BIOS Firmware setting page.

Why? Because what you have posted so far , is fragmented snippets of the total picture. Please help others, to be able to help you. They need to be able to know what they are making recommendations for.

As for posting photo's of output... That is useful, but... More useful and easier for you and others, is to cut and paste the text of the output into a post, between / wrapped within CODE Tags. That way Helpers can quickly see wht i going on, and can repost what they see, or make changes to, to show you 'what' to change, or whatnot.

---

### Post by username2758 on 2022-02-07
> **tea for one said:**
> Yes, you will need the EFI partition (sda1), assuming Ubuntu is installed in UEFI mode (which it should be)
When you have two drives each containing an OS, an EFI partition on each drive is highly desirable because each drive can be booted [COLOR=#0000FF]independently[/COLOR].

You can double-check the installation mode by booting into Ubuntu on sda, open a terminal and enter:-
```
[ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"

```

Thanks for the info! I'll be keeping the EFI partition.

```
ubuntubox@m75q:~$ [ -d /sys/firmware/efi ] && echo "UEFI mode" || echo "Legacy mode"
UEFI mode
ubuntubox@m75q:~$
```

---

### Post by username2758 on 2022-02-16
Hey,

So I took grahammechanical advice and started out by deleting sda7 which was my Linux Mint partition, and then expanded sda6 (which is my Ubuntu partition) into the unallocated space. The process was completed successfully!

I have deleted Windows partitions too and it is kind of confusing now. What should I do next?

Based on the screenshot of Gparted attached here, what should I do in order to increase the size of sda8 which is my data partition after deleting all Windows partitions? I want to keep sda6 (Ubuntu partition) only for testing so I I plan on reducing the size of it to something like 50GB to increase the size of sda8 (data partition) to as large as it can get.

> **grahammechanical said:**
> If you delete sda1 you will break Grub because sda1 is the efi boot partition. It contains Grub boot files as well as the Windows boot files. With Guid Partition Table (GPT) drives there has to be an efi boot partition to contain the boot files for the OS. It is FAT32 so that Windows boot files can be loaded from it as was well as Linux boot files. If you are sure that you no longer need Windows then you can delete sda2, sda3, sda4, sda5 & sda7.

I would do it one partition at a time and test if Ubuntu still loads. I would start with sda7 and expand sda6 into the unallocated space. GParted takes a long time doing its stuff and stacking up a list of delete, move & resize actions can take what seems to be a very long time. I get nervous waiting. So I like to do the changes one at a time and assure myself that I still have a working OS.

The Windows boot files will still be in the efi boot partition. I think that you can remove them by going into the UEFI settings utility but I have next to no experience of doing that.

Regards

---

### Post by username2758 on 2022-02-16
Hooooooray! After some fiddling around and a good 5 hours all operations were done successfully and Ubuntu still booting up on this  drive!

Thank you all for the help guys! :D

---

