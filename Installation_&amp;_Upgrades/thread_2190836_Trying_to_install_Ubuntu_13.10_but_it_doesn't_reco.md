---
title: "Trying to install Ubuntu 13.10 but it doesn't recognise free space on installation"
date: 2013-11-29
forum: Installation &amp; Upgrades
---

### Post by 1DGX81peAuJh on 2013-11-29
I am a first time linux user and trying to install Ubuntu as a dual boot. I shrunk the volume of the HDD in windows but it doesn't recognise that I did it on the installation wizard.

---

### Post by grahammechanical on 2013-11-29
You need to give a lot more information than this. What version of Windows? 7 or 8? How may partitions? Less or more than 4? What install option are you trying? Install alongside or Something Else? We also need to know the boot system of the machine. Is it BIOS or UEFI?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

---

### Post by 1DGX81peAuJh on 2013-11-29
I'm running Windows 7.
I think there were 4 partitions. (Excluding free space)
Install alongside didn't come up so I clicked on something else.
Its UEFI.

---

### Post by 1DGX81peAuJh on 2013-11-29
> **grahammechanical said:**
> You need to give a lot more information than this. What version of Windows? 7 or 8? How may partitions? Less or more than 4? What install option are you trying? Install alongside or Something Else? We also need to know the boot system of the machine. Is it BIOS or UEFI?

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Regards.

See previous post aswell.

The boot system is actualy bios as if I boot in that my windows installation is regcognised but I cannot install Ubuntu onto the HDD that has windows installed, only onto my backup drive.

[IMG]http://i.imgur.com/w5HpEt1.png[/IMG]

[IMG]http://imgur.com/hgrloP2[/IMG][IMG]http://i.imgur.com/hgrloP2.jpg[/IMG]

---

### Post by heir4c on 2013-11-29
If you can start Windows and try to resize/restore the partition again IN Windows. [COLOR="#FF0000"]So that you have back the old situation.[/COLOR]

After that you boot in the Ubuntu live-session and start gParted. Then take a screenshot of that and post it here.

I think you had already 4 partitions and then you can't make a 5th partition next to the 4 partitions, because you can only have 4 primary partitions.

---

### Post by Hakunka-Matata on 2013-11-29
Hi, welcome to the forums, you want to install Ubuntu on your hard drive? GOOD idea.[URL="http://askubuntu.com/questions/371487/is-it-safe-to-format-msftres-msftdata-and-hidden-partitions"]

http://askubuntu.com/questions/371487/is-it-safe-to-format-msftres-msftdata-and-hidden-partitions[/URL]

You may be able to get a better understanding of your system partitions through reading that thread.

As you have a second drive of 2TB?, you might want to consider shrinking that volume to create some free space and install Ubuntu there instead. 

Important things to consider before proceeding with a dual-boot installation:
[LIST]
[*]How important is your Windows installation to you?, do you have it backed up?, do you have your data backed up?  What happens if the install thrashes the complete drive, have a plan to proceed after that eventuality?
[*]A safe and simple method to get Ubuntu installed and get some experience using it, without endangering your Windows OS Installation is to use a second drive for the Ubuntu Installation.  Disable your windows drive, unplug the SATA cable and power, then install Ubuntu to the other drive.  After it working, plug up your Windows drive again, and change the 'boot options' in BIOS to choose which system you boot to.
[/LIST]

Good Luck,

heir4c:  He's already done that, check out the .png and .jpg files in post #4.

---

### Post by 1DGX81peAuJh on 2013-11-29
> **Hakunka-Matata said:**
> Hi, welcome to the forums, you want to install Ubuntu on your hard drive? GOOD idea.[URL="http://askubuntu.com/questions/371487/is-it-safe-to-format-msftres-msftdata-and-hidden-partitions"]

http://askubuntu.com/questions/371487/is-it-safe-to-format-msftres-msftdata-and-hidden-partitions[/URL]

You may be able to get a better understanding of your system partitions through reading that thread.

As you have a second drive of 2TB?, you might want to consider shrinking that volume to create some free space and install Ubuntu there instead. 

Important things to consider before proceeding with a dual-boot installation:
[LIST]
[*]How important is your Windows installation to you?, do you have it backed up?, do you have your data backed up?  What happens if the install thrashes the complete drive, have a plan to proceed after that eventuality? 
[*]A safe and simple method to get Ubuntu installed and get some experience using it, without endangering your Windows OS Installation is to use a second drive for the Ubuntu Installation.  Disable your windows drive, unplug the SATA cable and power, then install Ubuntu to the other drive.  After it working, plug up your Windows drive again, and change the 'boot options' in BIOS to choose which system you boot to. 
[/LIST]

Good Luck,

heir4c:  He's already done that, check out the .png and .jpg files in post #4.

I did think about installing it onto the second HDD but in an ideal world I'd rather have it on the 1 TB one (1TB is a WD black whereas the 2TB is a Samsung F4, massive performance difference between the 2.) Backup wise I run weekly backups that get stored onto the second HDD.
When I installed W7 onto the 1TB drive (It was originally on the 2TB) I screwed around with it to get rid of the 100MB system reserved partition on the windows disk manager, would that have any effect on installing Ubuntu onto that drive?

---

### Post by heir4c on 2013-11-29
> heir4c: He's already done that, check out the .png and .jpg files in post #4. 

No, that are the screenshots of the partitions now. I ask for screenshots when he turned the situation back to where he started before he make the 5th partition (I think he created a 5th partition).

---

### Post by Hakunka-Matata on 2013-11-29
You said:  "[COLOR=#000000]When I installed W7 onto the 1TB drive (It was originally on the 2TB) I screwed around with it to get rid of the 100MB system reserved partition on the windows disk manager, would that have any effect on installing Ubuntu onto that drive?"
[/COLOR]
I do not have a good answer for that question, I no longer waste my time playing chess with Windows Corporation.  I spent a lot of time maintaining Windows OSes and networks, it no longer entices me, there are MUCH smarter alternatives out there, Ubuntu is one of them.  I don't like how Windows Corporation plays, I don't lower myself to playing their game, their OS is confusing (on purpose I think), costly (in terms of time and money), and the whole philosophy of their organization smacks of avarice.  No likie!  So instead I use a lovely open source OS named Ubuntu, I try to encourage others to try it, (most who try it like it) and that's my game.  So check out the link below, it's a method of playing it safe when trying to mix the bad with the good, (Windows with Ubuntu).  As long as you have your product key and a Windows 7 ISO image file backed up somewhere, you'll be able to get your Windows 7 OS re-installed.  Data?, and programs?, that's something you have to think about as well.  Good backups are the safest and most efficient ways to play it safe.  It's your call.

 [http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html](http://www.pcworld.com/article/248995/how_to_install_windows_7_without_the_disc.html)

Once you're comfortable that you can recover, then you can proceed calmly with confidence no matter what happens, you're not going to be sorry. 
Do you understand that if you install Ubuntu on the same drive you have your Windows Installation on, Ubuntu is going to change how Windows gets started, via Grub.  Grub modifies the mbr ([Master Boot Record]("http://www.howtogeek.com/howto/32523/")), so that Windows will no longer be able to boot itself if you decide to delete the Ubuntu partition? If you learn how to repair it now, it's not that difficult, you  won't be disappointed and dismayed when you discover that is one of the consequences of installing Ubuntu as a dual boot system.

Ok, enough for now, the safe and simple way is to use a separate drive to install Ubuntu on.  Use a spare small drive if you have one, Ubu only needs about 30 GiB to make a useable system and data installation.

---

### Post by fantab on 2013-11-30
Boot with Ubuntu Live DVD/USb and "Try Ubuntu without installing", open Terminal and post the output of the follwoing:

```
sudo parted -l
sudo fdisk -l
```

---

### Post by Hakunka-Matata on 2013-11-30
fantab, I like your reply much more than my own.

---

### Post by 1DGX81peAuJh on 2013-11-30
> **fantab said:**
> Boot with Ubuntu Live DVD/USb and "Try Ubuntu without installing", open Terminal and post the output of the follwoing:

```
sudo parted -l
sudo fdisk -l
```

```
ubuntu@ubuntu:~$ sudo parted -l
Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table.
However, it does not have a valid fake msdos partition table, as it should.
Perhaps it was corrupted -- possibly by a program that doesn't understand GPT
partition tables.  Or perhaps you deleted the GPT table, and are now using an
msdos partition table.  Is this a GPT partition table?
Yes/No? yes                                                               
Model: ATA WDC WD1002FAEX-0 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  316MB   315MB   ntfs         Basic data partition          hidden, diag
 2      316MB   419MB   104MB                EFI system partition          boot
 3      419MB   554MB   134MB                Microsoft reserved partition  msftres
 4      554MB   1000GB  1000GB               Basic data partition          msftdata


Model: ATA SAMSUNG HD204UI (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  2000GB  2000GB  primary  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk! 
```

```
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x995b680c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1953519615   976758784    7  HPFS/NTFS/exFAT

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc8446c62

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907026943  1953512448    7  HPFS/NTFS/exFAT


```

---

### Post by 1DGX81peAuJh on 2013-11-30
> **heir4c said:**
> No, that are the screenshots of the partitions now. I ask for screenshots when he turned the situation back to where he started before he make the 5th partition (I think he created a 5th partition).

I didnt create a 5th partition I left it as free space but Ubuntu didn't recognise it as free space.

---

### Post by fantab on 2013-11-30
Are you able to boot Windows 8? 
How did you 'Shrink' Windows NTFS Partition?
You either have file system errors on all your partitions except the /dev/sda1 or your Partition table is corrupt.

Boot Windows and run [**CHDSK**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") on all partitions first. Do it a couple of times.
Then run the 'sudo parted- l' and post its output.

Also check if you have some sort of RAID, check in UEfI/BIOS under 'SATA MODE or SATA CONFIGURATION'.

---

### Post by heir4c on 2013-11-30
> **aaron.zelos said:**
> I didnt create a 5th partition I left it as free space but Ubuntu didn't recognise it as free space.

Ok, you did not format that free space, but it is the same. You have already 4 partitions, so you can't create a new one. (If it is free space or a formatted partition).
And that Ubuntu don't show that space, ok, but Windows don't show you the other 3 partitions, so, when a person see that he think I can create an other partition because there is only one.

I don't now what partition you can delete, that answer you will get from other members with knowledge about it. 
So, succes, I hope you can solve your problem with the help of the other members.

Greetings,
Gerolf

---

### Post by fantab on 2013-11-30
OP has GPT disk (/dev/sda). GPT does not LIMIT itself to 4 Primary partitions, you easily create more than 100 Primary Partitions. You don't have to delete any partition on GPT disk.
However, Ubuntu installer needs to see either a Linux Filesystem or 'Unallocated Space' to install to.

---

### Post by heir4c on 2013-11-30
Ok, fantab, ThanX for the info. I don't have/use the GPT (I heard about it, but that's all)

---

### Post by fantab on 2013-11-30
> **heir4c said:**
> Ok, fantab, ThanX for the info. I don't have/use the GPT (I heard about it, but that's all)

You are welcome. 

Advantages of GPT: [https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

---

### Post by 1DGX81peAuJh on 2013-11-30
> **fantab said:**
> Are you able to boot Windows 8? 
How did you 'Shrink' Windows NTFS Partition?
You either have file system errors on all your partitions except the /dev/sda1 or your Partition table is corrupt.

Boot Windows and run [**CHDSK**]("http://www.eightforums.com/tutorials/6221-chkdsk-check-drive-errors-windows-8-a.html") on all partitions first. Do it a couple of times.
Then run the 'sudo parted- l' and post its output.

Also check if you have some sort of RAID, check in UEfI/BIOS under 'SATA MODE or SATA CONFIGURATION'.

I can boot into windows fine.
I shrunk the partition using disk management.
Will edit with results soon.

---

