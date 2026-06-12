---
title: "Failed upgrade RAID mayhem"
date: 2012-05-16
forum: Installation &amp; Upgrades
---

### Post by Jimmy9pints on 2012-05-16
Hello there,

I had 11.10 installed on a RAID1 setup - FAKERAID apparently. 

Hit the upgrade button to migrate to 12.04 and it didn't complete. It totally stalled and never recovered. After waiting for a day or so, I had to hit reset and hope for the best. The system is totally unusable. 

I have used a live USB and attempted to install again on my / partition. It didn't work. When I go into the partitioner, Ubuntu can see both disks. Last time I installed it, I am sure the partitioner couldn't see both disks. The OS was tricked into thinking there was just one disk. 

```
mdadm
```
lists both disks too. 

Interestingly though, when I used the file browser, only one disk is listed. 

Anyway, I have tried installing it to just one disk - but it always throws up an error saying the swap space could not be created. 

So I am stuck. I can't reinstall. My system is completely unusable. 

I have read that I should not use Fake Raid, and rely on Linux's own software raid. I could do that, but I already have two mirrored disks so I don't know what steps I should take at this point. 

Any help appreciated. 

Thanks

Jimmy.

---

### Post by darkod on 2012-05-16
OK, hold on.

mdadm IS the software raid, not the fakeraid.

The fakeraid package is dmraid. If you are sure you had fakeraid, try this below, if not, ignore it and we can start with mdadm.

Lets start with basics. Boot into live mode, and in terminal try to activate the fakeraid:
sudo dmraid -ya

If you check what devices are present now, what does it show, any fakeraid device:
sudo parted /dev/sda print all

Post the output of this parted command anyway, it will show what partitions you've got.

---

### Post by choppyfireballs on 2012-05-16
> **Jimmy9pints said:**
> Hello there,

 

Interestingly though, when I used the file browser, only one disk is listed. 

Anyway, I have tried installing it to just one disk - but it always throws up an error saying the swap space could not be created.  

Jimmy.

First of all Darkod is correct fake is different than software and mdadm is software. I would try his above recommended, however when you tried to install to one hdd were both plugged in or were you just not trying to set up the raid, also you aren't going to be able to see both HDD's in the filebrowser as the filebrowser, at least for software is reading the raid array not a specific HDD. I may be stating it wrong but my point is that nautilus will not be able to browse to the second HDD unless you manually mount it through terminal or disk utility.

---

### Post by Jimmy9pints on 2012-05-21
Hi, thank you both for your replies. 

So, firstly just to clarify, I am aware of the difference between fake raid and software raid. I am 100% sure that when I originally installed Ubuntu I had set up a fake raid through the bios. Therefore, as you suggested I'll go with dmraid. 

Now I am booted into the liveUSB. 

> **darkod said:**
> OK, hold on.

mdadm IS the software raid, not the fakeraid.

The fakeraid package is dmraid. If you are sure you had fakeraid, try this below, if not, ignore it and we can start with mdadm.

Lets start with basics. Boot into live mode, and in terminal try to activate the fakeraid:
sudo dmraid -ya


OK so here's the output:

```
ubuntu@ubuntu:~$ sudo dmraid -ya
dmraid: invalid option -- 'y'

```

Hmm not so good. From the man page I got dmraid -ay, so:

```
ubuntu@ubuntu:~$ sudo dmraid -ay
RAID set "nvidia_egdadehd" already active
RAID set "nvidia_egdadehd1" already active
RAID set "nvidia_egdadehd5" already active
RAID set "nvidia_egdadehd6" already active

```

> **darkod said:**
> If you check what devices are present now, what does it show, any fakeraid device:
sudo parted /dev/sda print all

Post the output of this parted command anyway, it will show what partitions you've got.

OK, so we get quite a lot of output here, which is also what I am seeing on the partition GUI in the installer. 

```
ubuntu@ubuntu:~$ sudo parted /dev/sda print all
Model: ATA ST31000525SV (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  20.0GB  20.0GB  primary   ext4
 2      20.0GB  1000GB  980GB   extended
 5      20.0GB  24.0GB  3999MB  logical   linux-swap(v1)
 6      24.0GB  1000GB  976GB   logical   ext4


Model: ATA ST31000525SV (scsi)
Disk /dev/sdb: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  20.0GB  20.0GB  primary   ext4
 2      20.0GB  1000GB  980GB   extended
 5      20.0GB  24.0GB  3999MB  logical   linux-swap(v1)
 6      24.0GB  1000GB  976GB   logical   ext4


Model: Netac OnlyDisk (scsi)
Disk /dev/sdc: 4010MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4007MB  4007MB  primary  fat32        boot, lba


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/nvidia_egdadehd1: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
 1      0.00B  20.0GB  20.0GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/nvidia_egdadehd6: 976GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  976GB  976GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/nvidia_egdadehd5: 3999MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
 1      0.00B  3999MB  3999MB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/nvidia_egdadehd2: 980GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1024B   3999MB  3999MB  primary   linux-swap(v1)
 2      4000MB  980GB   976GB   extended
 5      4000MB  980GB   976GB   logical   ext4


Model: Linux device-mapper (mirror) (dm)
Disk /dev/mapper/nvidia_egdadehd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  20.0GB  20.0GB  primary   ext4
 2      20.0GB  1000GB  980GB   extended
 5      20.0GB  24.0GB  3999MB  logical   linux-swap(v1)
 6      24.0GB  1000GB  976GB   logical   ext4

```

Now, that confuses me. 

Where to go from here?
The installer still can't create the swap space. Am I choosing the wrong partition? Here's the error message:
> The creation of swap space in partition #1 of Serial ATA RAID nvidia_egdadehd2 (partition #2) failed.

Why won't the installer create the swap space (that incidentally is already there from the last installation). 

Thank you people. 

Jimmy.

---

### Post by darkod on 2012-05-21
Partition #2 is the extended partition. The swap partition is #5.

I guess you had 20GB for /, 4GB for swap and the rest as separate /home partition.

So, when reinstalling use the partition #1 as root, #5 as swap and #6 as /home (without formatting it of course).

In the installer manual partitioning there should be only one raid1 device, with the above partitions.

Although the parted printout also specifies more raid devices including the separate partitions as a raid device. I'm not sure if this is how it understands fakeraid, or the array is little bit messed up.

That's why for single boot systems I always prefer software raid, works much better. You would use fakeraid only if dual booting since you can't install windows on linux software raid.

---

### Post by Jimmy9pints on 2012-05-21
> **darkod said:**
> Partition #2 is the extended partition. The swap partition is #5.

I guess you had 20GB for /, 4GB for swap and the rest as separate /home partition.

So, when reinstalling use the partition #1 as root, #5 as swap and #6 as /home (without formatting it of course).

In the installer manual partitioning there should be only one raid1 device, with the above partitions.

Although the parted printout also specifies more raid devices including the separate partitions as a raid device. I'm not sure if this is how it understands fakeraid, or the array is little bit messed up.

That's why for single boot systems I always prefer software raid, works much better. You would use fakeraid only if dual booting since you can't install windows on linux software raid.

Now I know,  I too would prefer software raid. But I didn't know atthe point of the initial installation. Now I am stuck with this. 

The partitioning you suggested is exactly what I am trying for, but it always fails after not being able to create the swap space. 

I do have a spare external disk which I could copy over all the data and start again (this time with software raid) - but I would prefer not to and just be able to fix this as is. 

Jimmy

---

### Post by darkod on 2012-05-21
Even if you select partition #5 for swap?

Just make sure from all the choices you select the correct one. Maybe that's where you made an error last time.

That message you posted clearly says creating swap on #2 failed and that's perfectly normal since #2 is the extended partition, the container for the logical partitions. You don't use it directly for anything.

You use 1, 5 and 6. Never 2.

---

### Post by Jimmy9pints on 2012-05-22
Will try again. 

Thanks for your help and patience!

Jimmy

---

### Post by Jimmy9pints on 2012-05-25
Tried it exactly as you suggested. Failed again ;( the story's told through pictures.

---

### Post by darkod on 2012-05-26
Maybe something is messed up in the array. You said in the beginning that after the tried upgrade it never really worked, not even if you try to reinstall.

It might be much easier for you to get the data out (or maybe you have recent backup that you are satisfied with), create new blank msdos partition tables on the disks, wipe the dmraid data (just in case). put your bios sata mode in AHCI and do a software raid install this time.

That way you have made the switch once and for all. :)

After that put the data back and fine tune your 12.04 LTS system.

---

### Post by csantosbh on 2012-05-26
Hello there,
I have the very same issue with an intel rapid storage array fakeraid. I have already tried several other distributions (OpenSUSE 12.1, Fedora 16) and they all present a similar problem (more info [here]("http://forums.fedoraforum.org/showthread.php?t=280058") and [here]("http://forums.opensuse.org/english/get-technical-help-here/install-boot-login/475437-installer-doesnt-detect-existing-linux-partitions-raid-0-a.html")). I'm starting to suspect that this issue is related with the kernel 3.X family. I'll try to install an older version (say 11.04), let's see how it goes.

**Update:** By running the 11.04 installer, I noticed that the partitioner detected my old ubuntu installation, and offered me more installation alternatives (such as replace my 10.10 by 11.04), which didn't occur on 12.04 installer. Obviously, I did not proceed with 11.04 installation, since it is already old and soon will no longer be supported. Thus I can't tell for sure whether or not 11.04 would really install on my system.

---

### Post by yurx cherio on 2012-06-07
I had the same problem with the installer failing on mapping swap partition. I found a solution/workaround.

The installer erroneously recognized my RAID twice and I had the same raid partition listed twice (and some of them even 3 times) in the list of partitions. So I selected the last reference to the SWAP partition and marked "for use". Then I selected each preceding reference to that same swap partition and explicitly marked each of them not to be used. Same applies to the other duplicate partitions in the list.

My guess is that by default the installer uses all swap partitions it can find. Since I had only one partition but it was recognized and listed several times the installer was failing to initialize it more then once.

It is obviously a bug in the partitioning tool.

On the top of that you need to properly specify the bootloader partition/device. For example you have the following md devices listed:

/dev/mapper/isw_xxxxxx_ARRAY0
/dev/mapper/isw_xxxxxx_ARRAY0p1
/dev/mapper/isw_xxxxxx_ARRAY0p2
/dev/mapper/isw_xxxxxx_ARRAY0p4
/dev/mapper/isw_xxxxxx_ARRAY0p5

You need to install your grub into /dev/mapper/isw_xxxxxx_ARRAY0

---

