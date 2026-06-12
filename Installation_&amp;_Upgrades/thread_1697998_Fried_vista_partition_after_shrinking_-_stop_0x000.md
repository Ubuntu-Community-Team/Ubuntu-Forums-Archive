---
title: "Fried vista partition after shrinking - stop 0x0000007b"
date: 2011-03-01
forum: Installation &amp; Upgrades
---

### Post by bodselecta on 2011-03-01
I've been dual booting vista/ubuntu for a couple of years on a dell xps1530 laptop but after using ubuntu entirely now for the last 6 month I wanted to switch over to ubuntu completely and reclaim some of the 100gb free space still on the vista partition. I'd done a bit of reading, realised it was going to be a pain and went through the steps described.
disabling page file, system restore etc, running a defrag then doing the shrink in vista.

It worked initially, creating 10gb of unallocated space. I blue screened initially getting back to vista but was able to get in using the last configuration. I think I disabled a system storage driver which vista was complaining about and now it seems fried - stop 0x0000007b

I suppose this is really a vista question but I want rid, no need for it and i'm sick of the security worries. I don't care about any data on the vista partition but would like to restore a small vista partition (40gb?). 
If I use a full system restore (from the dell disks) will it reformat the whole drive and I'll lose ubuntu?
Is there anyway to format the partition from ubuntu, resize it then reinstall vista into the smaller partition afterwards?

I'm a developer not an OS guy so I hate going near disk utilities :)

Any ideas that could help I'd really appreciate it.....

edit: i no longer want to keep the vista partition but want to format and mount in ubuntu, using virtualbox for any win apps i need

---

### Post by Hakunka-Matata on 2011-03-01
[http://www.cgsecurity.org/wiki/TestDisk_Download]("http://www.cgsecurity.org/wiki/TestDisk_Download")

I've seen a lot of people say good things about TestDisk, might be an option.

GParted is a solid tool, but it's been so long since I installed a Windows system, I've forgotten how the partitioning proceeds in a windows install........

---

### Post by Mark Phelps on 2011-03-01
> I don't care about any data on the vista partition but would like to restore a small vista partition (40gb?). 
If I use a full system restore (from the dell disks) will it reformat the whole drive and I'll lose ubuntu?

Last time I restored a Dell, it provided no options for selecting location or size.  So, most likely it will either (1) reformat the drive and reinstall itself, or (2) fail and refuse to run -- because the partition size or location is different from the original.
> Is there anyway to format the partition from ubuntu, resize it then reinstall vista into the smaller partition afterwards?

You can use GParted to resize the Vista partition -- although, it's likely to corrupt it in the process.  But, unless you have Vista installation DVD, you're back to the first question of a custom restore -- which most likely, will not work.

---

### Post by Quackers on 2011-03-01
A 7b stop error can be caused by many things, but the last time I had one it turned out to be a faulty ram stick. Have you checked your ram?

---

### Post by lfforman on 2011-03-01
Just a simple question. Since you do not care for the vista or anything on it, why don't you complete delete the windows partion and install windows in a virtual machine? that is what I did.

---

### Post by bodselecta on 2011-03-01
Thanks for all the replies guys


> **Mark Phelps said:**
> Last time I restored a Dell, it provided no options for selecting location or size.  So, most likely it will either (1) reformat the drive and reinstall itself, or (2) fail and refuse to run -- because the partition size or location is different from the original.

You can use GParted to resize the Vista partition -- although, it's likely to corrupt it in the process.  But, unless you have Vista installation DVD, you're back to the first question of a custom restore -- which most likely, will not work.
This is what's worrying me, is vista basically redundant now?
Is the rule of thumb, windows first, linux later?


> **lfforman said:**
> Just a simple question. Since you do not care for the vista or anything on it, why don't you complete delete the windows partion and install windows in a virtual machine? that is what I did.
Funnily enough, that's what prompted this. Getting virtualbox running with various IE installs, so I needed more space. The biggest worry I've had with an Ubuntu only install is the poor Intel wifi drivers. It's better than previous releases but usually takes 3-5 reboots till the network driver wakes up
If I go down this path, is it just a case of formatting the partition and then assigning to ext4?


> **Quackers said:**
> A 7b stop error can be caused by many things, but the last time I had one it turned out to be a faulty ram stick. Have you checked your ram?
I haven't checked RAM, I'll do that next but the errors pointed to corrupt drivers. I'm just guessing but I'd thought that after disabling the storage driver was when it all went wrong and I'm guessing the storage driver is the pagefile? Another unintelligent guess is that something in the MBR is in the unallocated space?

```

Root cause found: 

---------------------------

Boot status indicates that the OS booted successfully.


Root cause found: 

---------------------------

A recent driver installation or upgrade may be preventing the system from starting.

```

---

### Post by lfforman on 2011-03-02
Basically if you wan't to eliminate Windows on a normal dual-boot set-up of ubuntu, just go to your prefered partion manager and delete the windows partion and create a new one as ext 4.

---

### Post by bodselecta on 2011-03-02
Ok, so coming to the conclusion that my existing vista install is gubbed and i won't be able to reinstall from the dell restore disks, there's no danger just reformatting the vista (sda3) partition to ext4?

From what i understand, the mbr points to grub and the mbr won't be wiped so shouldn't be a problem?
Is it just a case of formatting the vista partition on sda3 to ext4 then resize to include the unallocated space? 
How do i then move this partition to the sda4 where ubuntu is? Or do I have to mount it in ubuntu?


```

Model: ATA WDC WD2500BEVS-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      32.3kB  123MB   123MB   primary   fat16
 2      124MB   10.9GB  10.7GB  primary   ntfs
 3      10.9GB  153GB   142GB   primary   ntfs            boot
 4      163GB   250GB   86.6GB  extended                  lba
 6      163GB   244GB   80.4GB  logical   ext4
 7      244GB   247GB   3455MB  logical   linux-swap(v1)
 5      247GB   250GB   2683MB  logical   fat32


```

---

### Post by FoxEWolf on 2011-03-02
stop 0x0000007b can mean multiple things. The solution is to use GParted to resize the Vista Partition and then reinstall Vista on that partition. I am hoping you backed up your data and that you have the license key and documentation so that restoring that data won't be a hassle.

---

### Post by bodselecta on 2011-03-02
Thanks, I'm not going to bother trying to restore vista now as I don't use it but would like to reclaim all the disk space...

So is my thinking correct in regards to my last post?

> **FoxEWolf said:**
> stop 0x0000007b can mean multiple things. The solution is to use GParted to resize the Vista Partition and then reinstall Vista on that partition. I am hoping you backed up your data and that you have the license key and documentation so that restoring that data won't be a hassle.

---

