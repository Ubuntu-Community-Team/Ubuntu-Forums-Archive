---
title: "Installer does not detect Windows 7 (not because of GPT)"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by mvr2 on 2015-03-31
Hello,

yesterday I tried to install Ubuntu 14.10 along side Windows 7. But the installer didn't detect my Windows 7. 
Windows 7 is based on a BIOS (not UEFI) and the first OS on this SSD at all. I also have ~40gb unallocated free space for ubuntu... (see screenshot)

Following outputs from sudo fdisk -lu and sudo parted -l

parted error message: Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/loop0: 1 GiB, 1115594752 bytes, 2178896 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 477 GiB, 512110190592 bytes, 1000215216 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xca451367

Device     Boot  Start       End   Sectors   Size Id Type
/dev/sda1  *      2048    206847    204800   100M  7 HPFS/NTFS/exFAT
/dev/sda2       206848 922390527 922183680 439.7G  7 HPFS/NTFS/exFAT

Disk /dev/sdb: 3.8 GiB, 4007657472 bytes, 7827456 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x4a022e4f

Device     Boot   Start     End Sectors  Size Id Type
/dev/sdb1  *          0 2271359 2271360  1.1G  0 Empty
/dev/sdb2       2250448 2254991    4544  2.2M ef EFI (FAT-12/16/32)
```

```
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Crucial_CT512MX1 (scsi)
Disk /dev/sda: 512GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs         boot
 2      106MB   472GB  472GB  primary  ntfs


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel? c
Model:  USB DISK 2.0 (scsi)
Disk /dev/sdb: 4008MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags:
```

Why it does not detect Windows 7?

Thanks for your help

---

### Post by Vladlenin5000 on 2015-03-31
Boot Windows, check its drive for error using the Windows tool, and make sure you shutdown Windows and not hibernate.

---

### Post by grahammechanical on 2015-03-31
You are using the Something Else option and the installer has correctly detected the 2 Windows partitions (ntfs) and the unallocated space. Do you get the option to Install Alongside? If you get that option and select it the installer will most likely resize a Windows partition instead of using the unallocated space. Is that what you want?

My advice would be to run the Ubuntu live session and use Gparted to create an Extended partition out of that unallocated space. And then in the Extended partition create 2 Logical partitions, one of about 2GB for swap and the rest for Ubuntu.

Then when you run the installer and select the Something Else options you will see the extended partition and the two logical partitions inside it. Select the 38GB partition and click Change and fill in the dialog box.

Use As should be set to Ext4
Tick to format the partition
Mount point should be /
Click OK

Then select select the 2 GB partition and in the dialog box select Use As = swap and tick the box to format the partition. When you click OK you will be taken back to the partitions page and now, after checking that everything is as it should be, you can click install.

[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Regards

---

### Post by mvr2 on 2015-03-31
thanks for your replies :)

@**_[[COLOR=#000000]Vladlenin5000[/COLOR]]("http://ubuntuforums.org/member.php?u=1468732")_:** 
I already checked the drive for errors using the Windows tool - nothing wrong (since its brand new). I also shutdown windows and not hibernate ...

@[**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323"):
I can't install Ubuntu along side Windows 7 because Ubuntu installer doesn't detect it. Therefore it says something like 'no OS detected' and i can only format my SSD and install Ubuntu or something else...
So is my Windows 7 save if I install Ubuntu as you described (can I still use it after Ubuntu installation)?
And why doesn't the Ubuntu Installer detect Windows 7? This bothers me since my PC is brand new and software seems already ****ed up :(

thx for your help : )

---

### Post by yancek on 2015-03-31
I'm not clear as to why you are saying the installer doesn't detect windows when, as the image from the installer in your first post clearly shows two windows partitions, sda1 and sda2.  I would follow grahammechanical's suggestion and select the unallocated space from the 'Something Else' installation option to create partitions.  When you select to install, make sure you do NOT use sda1 or sda2 and you might explain where you see 'no os detected' because windows clearly shows in the installer.

---

### Post by mvr2 on 2015-03-31
pls look at the screenshot, usually there should be an option like "install alongside Windows 7" and the whole process should be a lot easier... 
but I will try the manuell way as described above

---

### Post by Mark Phelps on 2015-03-31
The problem with using the "alongside" option is that, although it is simpler, it is also very risky -- as shrinking the Win7 OS partition from the Ubuntu installer could easily result in filesystem corruption to Win7.  That will prevent Win7 from being able to reboot -- making it very hard to fix.

BEFORE you charge into installing Ubuntu, use the win7 Backup feature to create and burn a Win7 Rescue CD.  You might need this later to restore the Win7 boot loader if it becomes corrupted from the dual-boot install.

---

### Post by yancek on 2015-04-01
I've seen numerous posts here and elsewhere with this situation, the Install Alongside option is not there.  Usually it is because there is no free space but that doesn't seem to be the case with your system.  I'm not sure why else that might happen.  Using a manual (Something Else) option may be more difficult for someone new but as stated above, it is certainly less risky and gives the user much more control over what is happening.   Reviewing a tutorial such as the one below before beginning will give you a good idea of what to expect.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by mastablasta on 2015-04-01
I too didn't get that install alongside option (MBR partitioning, BIOS, enough unallocated disk space). however the install process went just fine with manual partitioning.

grahammechanical told you how to do it. create 2 partitions root& swap. install grub to sda. manual installation does not touch windows partitions unless you tell it to. since you will be doing all operations in the unallocated disk space you shouldn't have to worry about it.

---

### Post by mvr2 on 2015-04-01
didn't work for me :(

gparted gave this warning/error out:

ubuntu@ubuntu:~$ sudo gparted
Failed to get D-Bus connection: No connection to service manager.
Too few arguments.
======================
libparted : 3.2
======================
The driver descriptor says the physical block size is 2048 bytes, but Linux says it is 512 bytes. (cancel or ignore option)

Thats why I created the 2 partitions with the installer
1. around 34gb, primary, ext4, root (/)
2. around 4gb, logical, swap

then I started the installation. But after some minutes the progress bar stuck at 100% "creating ext4 filesystem on sda3"  (install window with the ubuntu tips and hints)  after ca 1 hour I shut it down, because I found nothing helpful on the web. 
Afterwards it booted directly into Windows ?!
What went wrong? Or am I just too stupid ](*,)

Edit: Finally I did it \\:D/:cool: ... I made a new Ubuntu (14.04 this time) Live-USB and installed it manually. Everything went well this time. After reboot directly into Ubuntu I updated grub (sudo update-grub) and can now choose between Ubuntu and Windows ...
Maybe the Live-USB my brother gave me is corrupt :evil:

---

