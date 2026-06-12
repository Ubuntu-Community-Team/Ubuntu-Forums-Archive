---
title: "Windows install error - unrecognized partition style"
date: 2011-10-09
forum: Installation &amp; Upgrades
---

### Post by maxmiaggi on 2011-10-09
Hello. I won't say I am new to ubuntu, I have around 2 months experience in working with it.

So last week, I had Windows 7 installed in my laptop, which wasn't working as expected. So I decided to remove it and reinstall it, but this time side by side with ubuntu.

So I downloaded Ubuntu 10.04 LTS and installed it in my laptop (I actually chose to remove everything and install ubuntu, my bad). So everything was proper till here, and then I made a partition. The screenshot explains it. Since Windows cannot be installed in ext4 file system, I made it as NTFS.

Now during installation of windows from its DVD, it pops up an error:
"Windows cannot be installed to Disk 0 Partition 3"
The details:
"Windows cannot be installed to this disk. The selected disk is of the GPT partition style"

Even though I format it then and there itself, the same error occurs. I even tried deleting the partition and recreating it, but with absolutely no success.

There is something called Partition Type - "Linux Basic Data Partition". I even tried changing it to "MBR Partition Scheme", "Microsoft Basic Data Partition", etc, but still no luck.

Now what am I supposed to do? How do I install windows in the partition? Please Help.

Thanks in advance.

---

### Post by LinuxFan999 on 2011-10-09
Are you using 32 bit or 64 bit Windows?

---

### Post by maxmiaggi on 2011-10-09
32 bit windows 7

---

### Post by LinuxFan999 on 2011-10-09
GPT is not supported by 32 bit Windows 7.

---

### Post by maxmiaggi on 2011-10-09
Well, I also have the DVD for 64 bit windows 7, but I prefer 32 bit since many of the softwares that I have are designed for 32 bit.

In that case, which partition style should I choose in order to install 32 bit windows?

---

### Post by LinuxFan999 on 2011-10-09
You will need the MBR partition style (Master Boot Record).

---

### Post by maxmiaggi on 2011-10-09
I tried that, but with no luck. The same error occurs. :(

---

### Post by LinuxFan999 on 2011-10-09
What motherboard do you have?

---

### Post by maxmiaggi on 2011-10-09
well, I have a Dell Studio 15 Core2duo, so dont have exact idea of the motherboard in it.
Btw, 32 bit windows used to work fine in it till last week

---

### Post by LinuxFan999 on 2011-10-09
How much memory do you have? if you have 4 Gigabytes or more, you should use the 64 bit version of Windows 7. 32 bit Windows software works in 64 bit Windows.

---

### Post by maxmiaggi on 2011-10-09
i tried it with 64 bit now, but same error.. windows can't install in a gpt partition. i even changed the partition scheme to mbr.
now what to do??

---

### Post by oldfred on 2011-10-09
Often tools do not totally remove the gpt data as it has backups where MBR does not. GPT is the newer improved partition type but Window 7 only works if booting from a new UEFI system that replaces BIOS. 

Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Best to backup partition table first:
sudo sfdisk -d /dev/sda > partssda.txt

---

### Post by maxmiaggi on 2011-10-10
I tried using fixparts, but the following is displayed:

```
mayank@mayank-laptop:~$ sudo fixparts /dev/sda
FixParts 0.8.0

Loading MBR data from /dev/sda

This disk appears to be a GPT disk. Use GNU Parted or GPT fdisk on it!
Exiting!

```

I double checked it. The partition scheme is MBR.

:confused: :( How to fix this problem?

---

### Post by oldfred on 2011-10-10
Post this, does it look like my sda(MBR/msdos) or my sdb (gpt)?
```
sudo parted /dev/sda unit s print
```

```
fred@fred-MavericDT:~$ sudo parted /dev/sda unit s print
[sudo] password for fred: 
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system  Flags
 1      63s         115330634s  115330572s  primary  ntfs         boot
 4      115330635s  156296384s  40965750s   primary  fat32
 2      156296385s  312576704s  156280320s  primary  ext3

fred@fred-MavericDT:~$ sudo parted /dev/sdb unit s print
Model: ATA MAXTOR STM316081 (scsi)
Disk /dev/sdb: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start      End         Size        File system     Name      Flags
 1      34s        16064s      16031s                                bios_grub
 2      16065s     51215219s   51199155s   ext4            MAVERICK
 3      51215220s  57352049s   6136830s    linux-swap(v1)
 4      57352050s  312576704s  255224655s  ext4

```

---

### Post by maxmiaggi on 2011-10-10
I get this:


```
mayank@mayank-laptop:~$ sudo parted /dev/sda unit s print
[sudo] password for mayank: 
Model: ATA ST9320423ASG (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system     Name          Flags
 1      2048s       312498175s  312496128s  ext4            Windows Main
 2      312498176s  330076159s  17577984s   linux-swap(v1)
 3      330076160s  625142414s  295066255s  ntfs            Windows Main
```

---

### Post by oldfred on 2011-10-10
It sure looks like a gpt disk.

You then need to use gdisk to convert it.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)

---

### Post by maxmiaggi on 2011-10-11
[QUOTE="oldfred"]It sure looks like a gpt disk.

You then need to use gdisk to convert it.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr](http://www.rodsbooks.com/gdisk/mbr2gpt.html#gpt2mbr)[/QUOTE]

Well, I went through the details, and downloaded GPT fdisk from SourceForge as described here:
[http://www.rodsbooks.com/gdisk/download.html](http://www.rodsbooks.com/gdisk/download.html)

The downloaded file is a rpm file, inside which there is a tarball. Now how to proceed and run it? The instructions on the site are way too much complicated for me. I couldn't comprehend them.

Thanks.

---

### Post by oldfred on 2011-10-11
If you go the the bottom of this page it has .deb downloads.

[http://www.rodsbooks.com/gdisk/download.html#sourcerpm](http://www.rodsbooks.com/gdisk/download.html#sourcerpm)

From a .deb you can just click on it and install. Ubuntu also has a older version in the repository that you can download.

---

### Post by maxmiaggi on 2011-10-12
Hello oldfred

I have used the gdisk to convert my gpt disk into mbr. Now, it looks somewhat like this:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA ST9320423ASG (scsi)
Disk /dev/sda: 625142448s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type     File system     Flags
 1      2048s       312498175s  312496128s  primary  ext4
 2      312498176s  330076159s  17577984s   primary  linux-swap(v1)
 3      330076160s  625142414s  295066255s  primary  ntfs

```But there is one problem. During reboot, it shows

```
error: no such partition.
grub rescue>
```And thus I am not able to boot up. Right now, I am using a LiveUSB. How to proceed now?

---

### Post by oldfred on 2011-10-12
After a partition change like that you almost always have to reinstall grub2's boot loader to the MBR. And sometimes you have to chroot into your install and do a full reinstall of grub.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
[https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files](https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files)
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by maxmiaggi on 2011-10-14
Hello oldfred

I reinstalled the grub and now I am able to boot into ubuntu. But there is one more problem. The windows still doesn't recognize the partition type. I have attached the screenshot when I open up 'Disk Utility'.

It shows EFI (FAT-12/16/32) (0xef) as the partition type. When I change it to HPFS/NTFS (0x07), then it shows the following error (screenshot attached).

Now what to do?

Thanks

---

### Post by oldfred on 2011-10-14
The efi is legitimate only for  a 100 to 200MB efi boot FAT32 partition. Usually in gpt.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

copy & paste PTsda.txt to here.

Is it sda3?

sudo sfdisk --print-id /dev/sda 3

Then you can change sda3 to type 83

sudo sfdisk --change-id /dev/sda 3 83

---

### Post by maxmiaggi on 2011-10-15
id 83 corresponds to linux. linux is installed in sda1. so I should also change it for sda1?

btw, I want to install windows to sda3. So, should I change the id to 83 (linux) or 07 (NTFS) ??

---

### Post by oldfred on 2011-10-15
OOPS, if sda3 is NTFS then you are correct it should be  7. 

sudo sfdisk --change-id /dev/sda 3  7

---

### Post by maxmiaggi on 2011-10-17
Thank You oldfred! Thanks a lot! You are great! That did it :):)

I owe you one! :)

---

### Post by oldfred on 2011-10-17
Glad you got it working. :)

---

