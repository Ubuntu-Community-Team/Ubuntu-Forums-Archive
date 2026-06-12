---
title: "Unable to boot from grub prompt or CD on Lucid"
date: 2011-08-24
forum: Installation &amp; Upgrades
---

### Post by SES1 on 2011-08-24
First, I know there are numerous threads on grub errors but I have tried all possible solutions and that's why I'm here.  My issue is that I'm not able to boot from the grub prompt as described for installing grub from a LiveCD [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD"). I can see grub is installed but is missing the kernal and other files.

```
grub> ls
(hd0) (hd0,1)

grub>set
?=0
color_highlight=
color_normal=
pager=
prefix=(hd0,1)/boot/grub
root=hd0,1

grub>ls (hd0,1)
	Partition hd0,1: Filesystem type fat, UUID 4271-2846

grub> ls (hd0,1)
boot/ dev/ proc/ sys/

grub>ls (hd0,1)/boot
grub/

grub>ls (hd0,1)/boot/grub
..lots of *.mod files

linux /vmlinuz root=/dev/sda1 ro
error: file not found.

grub>initrd /initrd.img
error: you need to load the kernal first.
```

I ran the boot_info script and the output is attached. From what I can tell it cannot even detect an OS being installed, but I've kept everything up to date and never had any issues. Everything was fine yesterday and now this. Also, I tried the Boot Repair CD and that did not work. 

Thanks in advance.

---

### Post by oldfred on 2011-08-24
It looks like your sda1 is your recovery partition and attemts to repair installed parts of grub to it.

But you are missing all the other partition(s).

Partitions not seen in gparted
[http://www.rodsbooks.com/missing-parts/index.html](http://www.rodsbooks.com/missing-parts/index.html)
Use parted rescue to restore missing partition details in post #22
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

enable the "universe" repository to download testdisk
System>Administration>Software Sources>Ubuntu Software.
Maverick the software sources is System, Administration, Update Manager, settings button on lower left.
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by SES1 on 2011-08-24
oldfred,

Thank you for your response and the links. Ironically, I ran TestDisk on an external hard drive yesterday and could not repair it. After I unmounted the external drive everything was working just fine until I restarted and that brought me to the grub rescue prompt. Clearly, I was only able to install part of grub to get to this point. I'll report back with my progress

---

### Post by SES1 on 2011-08-24
So, it appears that GParted thinks there are no partitions (image attached). And, I cannot see them with the parted ...

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print
Model: ATA ST3200822AS (scsi)
Disk /dev/sda: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  8601MB  8601MB  primary  fat32        boot, lba
```

or fdisk.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008220c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    16798319     8399128+   c  W95 FAT32 (LBA)
```

I think I should have a go at TestDisk at this point but I wanted to be cautious about making changes based on what I read in those previous posts.

---

### Post by SES1 on 2011-08-24
Well, I made some progress, sort of. Before running TestDisk I could not see any partitions, as I demonstrated in my previous post. I could see what I think are 6 partitions after running the analysis but unfortunately it said none could be restored. The main issue I see after running "Analyse" is a message saying the geometry is incorrect because heads per cylinder is 255 when it may be 240. It does show a swap partition after running Analyse, but that does not help I don't think. Images attached of the TestDisk results.

I'll admit these low level operations with the drives are new to me (hence the blow by blow, sorry). That's why I'm a little hesitant to reconfigure something without some input and more research. I think that I'll see what I can dig up in the archives/google. Thanks.

---

### Post by oldfred on 2011-08-24
Having 240 heads is pretty unusual now, most times it is 255. Is drive a 200GB or 300GB as the total sectors are important.

It looks like you had several versions, as several older partitions are close. Do you know what your partition table looked like before? Did you save any printouts, run bootinfoscript or have anything that might give a better idea of which of the start/end partitions are the ones you want to recover. You cannot recover overlapping ones, so you have to review starts & ends to see what makes sense. But you really want to restore the last version not a previous as then the data will not be valid.

---

### Post by SES1 on 2011-08-25
It is a 200GB drive that I can say for certain. I had a little hard time following you about which version to save. Unfortunately, I never ran the boot info script when things were working so I'm unclear how I would know which partition(s) to save. Perhaps the geometry tool in TestDisk could resolve this problem of overlaps?

---

### Post by srs5694 on 2011-08-25
I have a suggestion, but it's a shot in the dark: Try telling TestDisk that the disk is a GPT disk rather than an MBR disk (IIRC, TestDisk calls these "Intel" disks). I'm suggesting this because GPT doesn't use CHS addressing, so with any luck, TestDisk won't gripe about confusing CHS issues and might be able to restore your partitions.

If this operation is successful, you could either leave the disk as a GPT disk (which would be fine if the disk boots just Linux) or use [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) to convert it back to MBR form (which would probably be necessary if you dual-boot Windows from the disk).

As I say, this is a desperate shot-in-the-dark type of maneuver. I think it's got less than a 50% chance of success, but you've got very little to lose by trying at this point. If you've got important data on the disk, though, I strongly recommend you do a low-level backup of the entire disk before doing *anything* more with it. You'll need another disk of equal or greater capacity to do this, and the command would be:

```

sudo dd if=/dev/sda of=/path/to/backup/image-or-dev

```

In this case, /dev/sda would be the disk you've got now (which could become /dev/sdb when you attach another disk, so be sure to verify this!). /path/to/backup/image-or-dev could be /dev/sdb (or /dev/sda!) to do a raw copy to overwrite the whole disk, or it could be a file on a filesystem (to create an image file). Be very careful when specifying the if= and of= options; if you get them wrong, you could trash all the data on the disk you're trying to preserve!

---

### Post by SES1 on 2011-08-25
srs5694,

I do not have Windows installed at all on this computer only Lucid. So, restoring anything related to Windows is not a concern. The main concern I do have is rescuing my data from that hard drive. The problem I'm having does not seem that uncommon so hopefully I'll get/find some possible solutions. If I don't then I may try what you suggest but it sounds pretty risky.

---

### Post by srs5694 on 2011-08-25
I'd like to point out that you may be misinterpreting the problem; you've said several times that parted, GParted, and other tools can't see *any* partitions, but the output you've posted *does* show them recognizing *one* partition. This is a critical distinction because many problem reports about libparted-based tools showing no partitions are caused by a bug in libparted that creates the symptom of a *completely empty* partition table when in fact the partitions are defined but there's an error in the partition table. If the tool shows *any* partitions, you do *not* have this problem. I've got [a Web page](http://www.rodsbooks.com/missing-parts/index.html) that describes this symptom and one possible cause of it.

The point is that your partition table is *not* completely empty, so the cause is not the same. You won't be able to recover your partitions using the tools or techniques that would fix the libparted issue, so if you're investigating that possibility you're wasting your time. The only way to recover your partitions is to create new partition definitions of the correct size, and there are really only three ways to do this:


[list]
[*]Restore your partitions using a backup. This could be a backup made from a command like "sudo sfdisk -d > parts.txt", a binary backup of your MBR made with dd, or a printout of the partition table as shown by fdisk or some other utility. If you've got such a backup, now is the time to mention it.
[*]Scan your disk for filesystem signatures. This is what TestDisk does. GParted has a similar option, but IIRC it's more limited. (OTOH, in at least one case I've seen reported here, GParted was able to recover a partition that TestDisk couldn't.)
[*]Guess. The odds of this approach working are microscopic unless you can remember your partition sizes in sufficient detail to get it right, or if you can infer them based on the sizes and locations of other partitions.
[/list]


In theory, whether you tell TestDisk or other partition recovery utilities that you've got an MBR disk or a GPT disk is irrelevant. In either case, the tool will scan the disk for filesystem signatures and build a partition table from the detected filesystems. The reason I suggested telling TestDisk that your disk uses GPT is simply that the geometry mismatch error it's reporting is relevant only to MBR disks; thus, you might be able to bypass that problem by telling TestDisk to treat the disk as having originally been GPT.

---

### Post by SES1 on 2011-08-25
srs5694,

Thanks for taking the time to explain this issue, I'll definitely send you some support. I had never heard of the "sfdisk" command until I started having these problems so, I think the first option of having that sort of backup is probably out of the question. Following your recommendations for scanning the disk is what I'll try when I get home from work. The last option of guessing is kind of a black box to me, and I can't envision any way I could get that right without knowledge of how the partitions were before. Another thing that is unknown to me is what would happen if I were to guess wrong. Would I lose all my data and have to reformat/partition the drive somehow or would it incur a more serious/permanent change on the disk?

---

### Post by srs5694 on 2011-08-25
In the MBR scheme, creating a primary partition only modifies one sector on the disk (the MBR, where primary partitions are defined and where the MBR boot loader code lives), so if you generate nothing but primary partitions, guessing wrong will not trash data on your disk *provided* you don't try to *write* to the partitions you create.

If you create logical partitions, though, there is a small risk, because logical partitions are defined in data structures that appear just before the partitions they describe. Thus, if you guess wrong, you will have written a data structure to a sector that might actually be a critical part of some other partition. If you're lucky, though, even such a bad guess won't cause problems, since the sector you modify might just be unallocated space within another partition, or it might be unallocated space between partitions. It could also be part of a file, in which case you will have damaged a single file.

---

### Post by SES1 on 2011-08-25
I had to read that a few times for it to sink in. The logic is perfectly clear, it's just the concept of the disk partitions I'm grappling with. Anyway, step 1: backup the disk. From what I have read this may take around 8 hours but I'll just have to wait and see. Either way, I'll have a few things to try tomorrow and a copy of my drive to fall back on if things go awry. Thanks.

---

### Post by SES1 on 2011-08-26
Okay, I tried telling TestDisk that I have a GPT partition type but I don't think that solved the problem. After searching to only about 5% of the disk in quits and shows one partition

```

TestDisk 6.12, Data Recovery Utility, May 2011 
 Christophe GRENIER <grenier@cgsecurity.org> 
 http://www.cgsecurity.org 
  
 Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63 
  
 The harddisk (200 GB / 186 GiB) seems too small! (< 2077 GB / 1935 GiB) 
 Check the harddisk size: HD jumpers settings, BIOS detection... 
  
 The following partition can't be recovered: 
      Partition               Start        End    Size in sectors 
 >  Mac HFS                 20547534 4057992956 4037445423 [&#65533;d~I&#65533;>&#65533;W&#1314;&#65533;*SYo&#65533;e] 



[ Continue ]
HFS, 2067 GB / 1925 GiB
  
 
```The results of the initial analysis.

```

TestDisk 6.12, Data Recovery Utility, May 2011 
 Christophe GRENIER <grenier@cgsecurity.org> 
 http://www.cgsecurity.org 
  
 Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63 
      Partition               Start        End    Size in sectors 
 >D MS Data                       63   16798310   16798248 [NO NAME] 
  D MS Data                     2046  389302269  389300224 
  P Linux Swap             389304320  390721519    1417200 
 
```When I chose to do a deeper search under the GPT partition type there were initially a number of errors.

```

Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4015834    4018713       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4021066    4023945       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4025258    4028137       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4032282    4035161       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4047914    4050793       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4061482    4064361       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4075690    4078569       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4092458    4095337       2880 [NO NAME] 
 Bad root_cluster 
 check_FAT: Unusual media descriptor (0xf0!=0xf8) 
 Warning: Incorrect number of heads/cylinder 2 (FAT) != 255 (HD) 
 Warning: Incorrect number of sectors per track 18 (FAT) != 63 (HD) 
   MS Data                  4109226    4112105       2880 [NO NAME] 
  
```But, these went away as the search progressed. The final results of the deeper search is below.

```

TestDisk 6.12, Data Recovery Utility, May 2011 
 Christophe GRENIER <grenier@cgsecurity.org> 
 http://www.cgsecurity.org 
  
 Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63 
      Partition               Start        End    Size in sectors 
 >D MS Data                       63   16798310   16798248 [NO NAME] 
  D MS Data                       69   16798316   16798248 [NO NAME] 
  D MS Data                     2046  389302269  389300224 
  D MS Data                     2048  389302271  389300224 
  D MS Data                    10243  389310466  389300224 
  D MS Data                  4015834    4018713       2880 [NO NAME] 
  D MS Data                  4021066    4023945       2880 [NO NAME] 
  D MS Data                  4025258    4028137       2880 [NO NAME] 
  D MS Data                  4032282    4035161       2880 [NO NAME] 
  D MS Data                  4047914    4050793       2880 [NO NAME] 
  D MS Data                  4061482    4064361       2880 [NO NAME] 
  D MS Data                  4075690    4078569       2880 [NO NAME] 
 Structure: Ok.  Use Up/Down Arrow keys to select partition. 
 Use Left/Right Arrow keys to CHANGE partition characteristics: 
                 P=Primary  D=Deleted 
 Keys A: add partition, L: load backup, T: change type, P: list files, 
      Enter: to continue 
 FAT32, 8600 MB / 8202 MiB 
 
```Unfortunately, all of this is giving me less of an impression of what is going on or what to do next. I tried to download the fixparts software but I'm seeing novel behavior from the package manager when running off of a CD.  That is, even if I try apt-get upgrade, I get the following errors.

```

dpkg (subprocess): failed to exec dpkg-deb to extract control information: Input/output error
dpkg: error processing /var/cache/apt/archives/foomatic-filters_4.0.4-0ubuntu1.1_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg (subprocess): failed to exec dpkg-deb to extract control information: Input/output error
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.32-33-generic_2.6.32-33.72_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg (subprocess): failed to exec dpkg-deb to extract control information: Input/output error
dpkg: error processing /var/cache/apt/archives/apt_0.7.25.3ubuntu9.6_i386.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)

```That means I can't open a package, and can't install build-essential so I could build a package from source. Is there a binary package somewhere? Or, is there a better way to proceed?

---

### Post by srs5694 on 2011-08-26
FixParts isn't likely to do you any good; it's designed to fix certain very specific problems and do certain very specific tasks, none of which appears to apply to you. Thus, I recommend you not bother with it.

Your deep analysis with TestDisk is more promising, but inconsistent and confusing. Let's start with the initial analysis:

```
Disk /dev/sda - 200 GB / 186 GiB - CHS 24321 255 63 
      Partition               Start        End    Size in sectors 
 >D MS Data                       63   16798310   16798248 [NO NAME] 
  D MS Data                     2046  389302269  389300224 
  P Linux Swap             389304320  390721519    1417200

```

The first of those partitions is *almost* the one that already exists on your disk, as revealed by your Boot Info Script output. TestDisk says it ends a few sectors earlier than Boot Info Script does. This probably reflects a filesystem that's a tiny bit smaller than the partition, since filesystems sometimes grow in increments that are larger than sectors. Thus, rewriting it as TestDisk suggests is *probably* OK, but I can't promise that. Boot Info Script says this is a FAT partition.

Unfortunately, the second partition (which begins at sector 2046) overlaps the first one, so both can't be configured simultaneously. It's unclear from the TestDisk data you've posted what filesystem it contains. TestDisk says it's of type "MS Data," but that looks like the partition type code, not the filesystem type, and on GPT disks, Linux has used Windows' partition type code until *very* recently, so that's not really very diagnostic.

The third partition is a Linux swap partition, and it's probably legitimate, but also not very interesting.

Do you know if your disk had an ~8GiB FAT partition at the start initially? If so, you can eliminate TestDisk's second partition as a legitimate possibility, but that puts you back at Square One, since TestDisk didn't find anything that might begin near the end of that partition.

If you did *not* originally have an ~8GiB FAT partition at the start of the disk, my inclination would be to tell TestDisk to recover the partitions that begin at sectors 2046 and 389,304,320, or to re-create them manually using fdisk (for MBR) or gdisk (for GPT). You could then try mounting the 2046 partition read-only using an emergency disk to see if it looks legitimate. If not, try again by manually creating and attempting to mount the 2048 partition or the 10243 partition. (FWIW, a partition that starts at sector 2046 is legal but unusual. A much more common start point is 2048.)

If you get a working partition in this way, you may need to re-install GRUB. If you go with GPT, this will go more smoothly if you first create a [BIOS Boot Partition.](http://en.wikipedia.org/wiki/BIOS_Boot_partition) I just want to provide this pointer now, but not go into too much detail, since you should be focusing on partition recovery at the moment. Getting the system booting again is the next task.

---

### Post by SES1 on 2011-08-26
This is going to sound odd but I found my entire ubuntu installation, directories and all, using an older version of TestDisk! I just need to figure out how to correctly write the partition table and then work on trying to get things to boot. Here is what it looks like:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 200 GB / 186 GiB - CHS 24322 255 63
      Partition                           Start              End       Size in sectors
D FAT32 LBA                        0    1   1  1045  164 54       16798248 [NO NAME]
D Linux                                0  32 33 24232  241 9      389300224 


``` 

When I look into the "FAT32" partition I see:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
            FAT32 LBA                          0         1   1    1045 164 54      16798248 [NO NAME]
Directory /
drwxr-xr-x        0            0               0 24-Aug-2011 12:05 boot
drwxr-xr-x        0            0               0 24-Aug-2011 16:01 dev
drwxr-xr-x        0            0               0 24-Aug-2011 16:01 proc
drwxr-xr-x        0            0               0 24-Aug-2011 16:01 sys

```

This clearly is something I created in an attempt to install GRUB from the LiveCD, based on all the GRUB threads I read through, thinking that was the only issue. If I look in the boot directory here for example, I see nothing but a grub/ folder (which is exactly the results I showed in my initial post in this thread). 

However, if I look into the Linux partition:

```

TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org
         Linux                                       0  32 33 24232 241   9  389300224
Directory /
drwxr-xr-x          0            0             4096 23-Aug-2011 20:27 .
drwxr-xr-x          0            0             4096 23-Aug-2011 20:27 ..
drwx------         0            0           16384 19-Jun-2010  22:54 lost+found
drwxr-xr-x          0            0             4096 22-Jun-2010  03:10 var
drwxr-xr-x          0            0           12288 24-Aug-2011 00:05 etc
drwxr-xr-x          0            0             4096 22-Dec-2010 20:56 media
drwxr-xr-x          0            0              4096  1-Aug-2011 22:53 bin
drwxr-xr-x          0            0              4096 11-Aug-2011 22:57 boot
drwxr-xr-x          0            0              4096 29-Apr-2010 12:19 dev
drwxr-xr-x          0            0              4096 19-Jun-2010 23:21 home
drwxr-xr-x          0            0            12288  3-Aug-2011 19:41 lib
drwxr-xr-x          0            0              4096 23-Apr-2010 10:11 mnt
drwxr-xr-x          0            0              4096   2-Feg-2011 21:24 opt
drwxr-xr-x          0            0              4096 23-Apr-2010 10:11 proc
drwxr-xr-x          0            0              4096 12-Feb-2011 02:25 root
drwxr-xr-x          0            0              4096 23-Feb-2011 10:07 sbin
drwxr-xr-x          0            0              4096   5-Dec-2009 21:55 selinux
drwxr-xr-x          0            0              4096 18-Jan-2011  00:15 srv
drwxr-xr-x          0            0              4096 30-Mar-2010 07:17 sys
drwxrwxrwt          0            0              4096 24-Aug-2011 00:05 tmp
drwxr-xr-x          0            0              4096 27-Mar-2011 16:45 usr
lrwxrwxrwx          0            0                  34 18-Jul-2011   14:23 vmlinuz
lrwxrwxrwx          0            0                  34 18-Jul-2011   14:23 initrd.img
drwxr-xr-x          0            0              4096 19-Jun-2010 23:11 cdrom
-rw-------         0            0                     0 23-Aug-2011 20:27 sqlQ5Qi7X
lrwxrwxrwx          0            0                  37 22-Jun-2011 20:38 initrd.img.old
lwrxrwxrwx          0            0                  34 22-Jun-2011 20:38 vmlinuz.old

``` 

And when I look into /boot I see all the linux kernels. This seems odd I guess to have one partition but I vaguely recall setting up ubuntu on the whole drive because that is the only OS I wanted to run (maybe this was wrong?). I know this is the correct partition because I looked in the /home dir and saw my user folder and in it was all my data! Anyway, how would you write the partition table and approach rebooting? Set "Linux = *" the primary bootable drive? I guess from there perhaps I could go through the LiveCD procedure to try and get GRUB installed so I can reboot? Many thanks, this is looking a lot better!

---

### Post by srs5694 on 2011-08-26
Actually, the partitions recovered by the old TestDisk version are close to those recovered by your earlier GPT attempt. Translated from the insane and obsolete CHS system that TestDisk insists on continuing to use, the two partitions you recovered have LBA sector values of:

FAT32: 63 - 16,798,310
Linux: 2048 - 389,302,271

The first of those is the same as the FAT32 partition recovered by the GPT attempt and the second one is the partition that begins on sector 2048 from that attempt.

Note that these partitions have the same problem I noted in my last response: They overlap. Thus, they can't *both* be correct. Given your description, I strongly suspect that the 2048 partition is valid and the 63 partition is old data from your earlier attempt to install Linux. (Linux doesn't normally use FAT32 partitions except for data exchange purposes with other OSes.)

I've only used TestDisk once or twice myself, so I don't recall its menus very clearly; but somewhere there should be an option to write selected partition definitions to disk. You can use that to do the job. Alternatively, you could use fdisk (for MBR) or gdisk (for GPT) to write the Linux partition definition. Just be sure that you enter the sector values precisely and that the program accepts the values you enter without modifying them. (If using fdisk, you may need to launch it with the "-l" option, as in "sudo fdisk -l /dev/sda". Otherwise most versions of fdisk use cylinder measurements by default, rather than sector values.)

Your latest attempt has not recovered a swap partition, but your GPT attempt did. This isn't a big deal, but you may want to create a fresh swap partition and adjust /etc/fstab appropriately when you're done.

---

### Post by SES1 on 2011-08-26
True, I can't see a swap partition now but I feel like that is small potatoes compared to not seeing an OS at all. Now I can see all of my directories and files just as I had them laid out so, I feel very confident that the "Linux" partition is correct. I will definitely want to straighten this out though (once I can reboot). 

As I alluded to earlier, it's just an odd way to proceed because no examples show having a single primary/bootable partition. I've got everything backed up so I'll write the table and reboot and see what happens. Presumably, I'll be back at the grub> or grub rescue> prompt since I apparently had GRUB issues before. Perhaps having the partition table written correctly would allow me to boot from grub? We'll find out shortly :)

---

### Post by SES1 on 2011-08-26
srs5694,

I was not clear in my last post. What was trying to get at (based on the TestDisk menu) is whether the "Linux" partition table would be better written as Primary ("P") or Primary bootable ("*")? I would have to guess Primary bootable since there is only one. Right? Keeping the FAT32 partition is not an option, exactly as you described, because they overlap.

---

### Post by srs5694 on 2011-08-26
I'm not familiar enough with TestDisk to know every detail of the terminology it uses; however, "bootable" generally refers to a particular bit that's set in a partition's entry to flag it as bootable for certain boot loaders. GRUB ignores this flag, and Linux does, too, so it shouldn't matter whether or not it's set on most Linux-only installations. A few BIOSes, though, won't boot unless they see a partition with a boot flag set. Therefore, if I understand the option, either will probably work, but "primary bootable" may be preferable if you've got one of these buggy BIOSes. (They're common on Intel-branded motherboards, FWIW.)

---

### Post by oldfred on 2011-08-26
Grub does not use boot flag, Windows & Lilo use boot flag to know which partition to boot from. 
A few BIOS check before booting to see if there is a boot flag on a primary partition, so it is best to have a boot flag on a primary partition, but for grub/Ubuntu it does not have to be the partition you boot from.

---

### Post by SES1 on 2011-08-27
Okay, thanks. Well, I *may* have the partition correct now but I have come full circle. After I reboot I'm back at the grub rescue prompt.

```

error: unknown filesystem.
grub rescue> ls
(hd0) (hd0,1)
grub rescue> ls (hd0)
error: unknown filesystem.
grub rescue> ls (hd0,1)
error: unknown filesystem. 

```

I guess this problem was not resolved so it's not surprising. The only thing I can think of, based on what I have read, is to try and do a grub-install from the LiveCD so I can reboot. Does this sound reasonable? I'm hesitant because I tried this initially and it did not work.

---

### Post by srs5694 on 2011-08-27
> **oldfred said:**
> Grub does not use boot flag, Windows & Lilo use boot flag to know which partition to boot from. 

Actually, LILO does *not* use the boot flag; however, if LILO (or GRUB, for that matter) is a secondary boot loader installed in a partition rather than in the MBR, then the MBR code *may* use the boot flag, depending on the MBR boot loader's design. In that case, you'd want the boot flag set on the partition to which LILO (or GRUB) is installed.

[quote=SES1]The only thing I can think of, based on what I have read, is to try and  do a grub-install from the LiveCD so I can reboot. Does this sound  reasonable? I'm hesitant because I tried this initially and it did not  work.[/quote]

Before you try that, I strongly recommend booting with a rescue disc of some sort and running the Boot Info Script again. That will provide diagnostic information that may be very important. For instance, the partitions may not have been defined in the way you expected, in which case you should re-create them in the proper way before doing anything else.

---

### Post by SES1 on 2011-08-27
Okay, here is the results of the boot_info script.

```
                  Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.97-1.98) is installed in the MBR of /dev/sda and looks at sector 
    1 of the same hard drive for core.img. core.img is at this location and 
    looks in partition 1 for /boot/grub.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.3 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   389,302,271   389,300,224  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        ff7d9784-e3e7-4546-9ede-4c504e3cff68   ext4       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-33-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-33-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-33-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-33-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-32-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-32-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-32-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-32-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-31-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-31-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-31-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-31-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-30-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-30-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-30-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-30-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-29-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-29-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-29-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-29-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-28-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-28-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-28-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-28-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-27-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-27-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-27-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-27-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-26-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-26-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-26-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-26-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-25-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-25-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-24-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-24-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-23-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-23-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
menuentry 'Ubuntu, with Linux 2.6.32-22-generic-pae (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    echo    'Loading Linux 2.6.32-22-generic-pae ...'
    linux    /boot/vmlinuz-2.6.32-22-generic-pae root=UUID=ff7d9784-e3e7-4546-9ede-4c504e3cff68 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-22-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set ff7d9784-e3e7-4546-9ede-4c504e3cff68
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###
--------------------------------------------------------------------------------

=============================== sda1/etc/fstab: ================================

--------------------------------------------------------------------------------
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=b67a6e10-4ad4-4585-a412-fbcd07be473c none            swap    sw              0       0
--------------------------------------------------------------------------------

=================== sda1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

  64.126674652 = 68.855492608   boot/grub/core.img                             1
 112.344318390 = 120.628793344  boot/grub/grub.cfg                             1
   0.936080933 = 1.005109248    boot/initrd.img-2.6.32-22-generic-pae          1
  64.149097443 = 68.879568896   boot/initrd.img-2.6.32-23-generic-pae          1
  64.273052216 = 69.012664320   boot/initrd.img-2.6.32-24-generic-pae          1
  64.258350372 = 68.996878336   boot/initrd.img-2.6.32-25-generic-pae          1
   5.430664062 = 5.831131136    boot/initrd.img-2.6.32-26-generic-pae          2
  64.320854187 = 69.063991296   boot/initrd.img-2.6.32-27-generic-pae          1
  64.328231812 = 69.071912960   boot/initrd.img-2.6.32-28-generic-pae          1
  16.832328796 = 18.073575424   boot/initrd.img-2.6.32-29-generic-pae          2
  17.679248810 = 18.982948864   boot/initrd.img-2.6.32-30-generic-pae          2
  12.042774200 = 12.930830336   boot/initrd.img-2.6.32-31-generic-pae          2
  15.981445312 = 17.159946240   boot/initrd.img-2.6.32-32-generic-pae          2
  64.350814819 = 69.096161280   boot/initrd.img-2.6.32-33-generic-pae          1
  64.134471893 = 68.863864832   boot/vmlinuz-2.6.32-22-generic-pae             1
  64.140110016 = 68.869918720   boot/vmlinuz-2.6.32-23-generic-pae             1
  64.152980804 = 68.883738624   boot/vmlinuz-2.6.32-24-generic-pae             1
  64.164165497 = 68.895748096   boot/vmlinuz-2.6.32-25-generic-pae             1
  64.158668518 = 68.889845760   boot/vmlinuz-2.6.32-26-generic-pae             1
  64.172004700 = 68.904165376   boot/vmlinuz-2.6.32-27-generic-pae             1
  64.175891876 = 68.908339200   boot/vmlinuz-2.6.32-28-generic-pae             1
  64.181518555 = 68.914380800   boot/vmlinuz-2.6.32-29-generic-pae             1
  64.262241364 = 69.001056256   boot/vmlinuz-2.6.32-30-generic-pae             1
  64.276943207 = 69.016842240   boot/vmlinuz-2.6.32-31-generic-pae             1
  64.280830383 = 69.021016064   boot/vmlinuz-2.6.32-32-generic-pae             1
  64.332118988 = 69.076086784   boot/vmlinuz-2.6.32-33-generic-pae             1
  64.350814819 = 69.096161280   initrd.img                                     1
  15.981445312 = 17.159946240   initrd.img.old                                 2
  64.332118988 = 69.076086784   vmlinuz                                        1
  64.280830383 = 69.021016064   vmlinuz.old                                    1

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

It looks like the partition is defined correctly from what I can tell with /dev/sda1 as "*" boot partition and starting at 2048. Also, I noticed there is some output about how the swap was on /dev/sda5.

---

### Post by oldfred on 2011-08-27
Actually boot script now looks normal to me. You are missing the swap partition that it is trying to mount, but that should only give an error on booting and still let you boot.

Not sure why boot script shows and mounts sda1 ok, but grub does not.
You may just need to reinstall grub2's boot loader or try manual boot. You may need to run a filecheck on sda1 since something still may be slightly out of order.

#From liveCD so everything is unmounted,swap off if necessary, change sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:

sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

You then should create your swap and will have to update fstab with new UUID.

---

### Post by srs5694 on 2011-08-27
I don't have anything to add to oldfred's suggestions at this time. (I just thought I'd post this in case you were waiting for multiple responses before proceeding.)

---

### Post by SES1 on 2011-08-27
Thank you both. I'll give it a shot now...

---

### Post by SES1 on 2011-08-27
SUCCESS!!!! :P

After I rebooted and did update-grub I rebooted again just  to make sure everything was working. I have one last question about this issue and one general question.

> **oldfred said:**
> You then should create your swap and will have to update fstab with new UUID.

Do I go about this with GParted or a similar tool and just specify the size of the swap? Does the fstab file need to be updated manually? Last, I have a brand new external drive I bought to get me through this process and now I'd like to backup the whole drive, not just some files. Since all hard drives come with installers for PC and Mac what is the best way to go about backing up once everything is correct. The "dd" command or is there another tool out there?

---

### Post by oldfred on 2011-08-27
That is great news.:)

You need to use liveCD's gparted to create swap. You may be able to do it from your install since you only have sda1, but it is always best to use liveCD for gparted to make sure everything is not mounted. (Even then you often have to unmount swap with a swapoff right click - but you do not have it yet)

create swap, the reboot. this will show UUID
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

Then run this to remount from fstab to make sure there are no errors in editing. If it just returns, it is ok or else it will report errors.

sudo mount -a

You may want to backup partition table or run boot script to document  entire system.
sudo sfdisk -d /dev/sda > PT.txt

I do not use dd very much. Its nickname is Data Destroyer. If you type anything wrong, it can cause a lot of damage. Since I do a lot of typos I avoid it.
My backup strategy is just to reinstall since I can do that in less than an hour and only back up my data, /home and some settings. But some like full backups and I have seen these suggested.

discussion of alternatives/strategy:
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

Full image backups
[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)
Tar backup script:
[https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html](https://help.ubuntu.com/11.04/serverguide/C/backup-shellscripts.html)

I modified this for my use:
Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

---

### Post by SES1 on 2011-08-27
Thanks oldfred! Based on your instructions and those online I should be able to manage fixing the swap issue and getting things backed up. I only really want what is in my /home folder so maybe it would be faster/easier to just do a clean install in the future. I'm going to mark this one solved and if I have major issues I'll start a new thread since that is really a different issue from the title of this thread. 

Many thanks to all!!

---

