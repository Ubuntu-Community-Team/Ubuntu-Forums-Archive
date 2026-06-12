---
title: "Switching to Ubuntu without losing the data on my NTFS partitions"
date: 2007-02-12
forum: Installation &amp; Upgrades
---

### Post by kag on 2007-02-12
I currently have the following setup in Windows XP (in this order):

First channel, master HD:
C: 25GB NTFS for Windows
D: 99.04GB NTFS for general data and game installs
E: 25GB for NTFS my CD collection

First channel, slave HD:
F: 149.05GB NTFS for general storage

Drive D: and E: could be merged into one partition if it would simplify the process.

I would like to switch to Ubuntu and kill Windows completely without loosing my data (except my C: drive obviously).

I would still like to have access to my data if I were to install Windows for whatever reason, so should I convert drive D, E and F from NTFS to FAT32?

What about the current C: partition, should I format it to ext3??

I'm a bit confused about all the partitions (when I used FreeBSD on my other test box, I had /, /usr, /var, and so on... will they all "fit" in the current allocated space for C:)

---

### Post by IgnorantGuru on 2007-02-12
I generally keep Ubuntu on a 5G partition.  It's currently 55% filled.  Depends on how much software you install, of course, but 25G should be plenty!

When I install Ubuntu with the alternate install CD (liveCD is probably similar), when it gets to the partitioner and wants to erase the entire hard disk, I select "manually edit the partition table".

You need one partition for the system (/), plus a linux swap partition (about double the size of your RAM, so if you have 1G RAM make it 2G).

So I suggest deleting the 25G partition.  Then create a new root partition, format it with Reiser or ext3 (I use reiser - faster and haven't had problems), and set mount point to /    Maybe use 20G-22G for that.

Then create a linux swap partition and use the remaining 3-5G.

Then select your NTFS partitions and set the mount points to something like /mnt/data, /mnt/cddata, /mnt/general.  DO NOT FORMAT them.

FYI, the installer failed to mount my NTFS partitions on a recent install - gave an error.  So I just removed the mount points during the install, and later added something like this to /etc/fstab:
```

/dev/hda3            /mnt/winxp           ntfs       defaults     0 0
```
(If your drive is SATA, then use /dev/sda# instead of hda#)

AFAIK, by default Ubuntu will only read ntfs partitions, won't write to them.  It will read/write to FAT32.  There is also a new ntfs3g driver that provides read/write access to ntfs.  You can read about that here...   [http://swik.net/ntfs3g](http://swik.net/ntfs3g)     I haven't tried that but it's supposed to work.

If you install Windows, it will be able to read/write NTFS or FAT32.  AFAIK it won't read ext2, ext3 or reiser (I'm sure about reiser but not positive about ext2/3, so don't quote me).

Another option would be to create 2 system partitions of 10G each, plus a swap partition.  That way if you want to try out a new version of Ubuntu you can test it in the unused partition.  Or if you later want to install Windows (yuck!), it can go there.  In fact, with 25G you could even create three 7G system partitions (two for future use).  FYI WinXP will fit comfortably in 7G, but AFAIK must be installed to a primary partition.  Linux can be installed to an extended partition.

However, you can have up to 4 primary partitions.  If you want more on the drive, you have to make the 4th an extended partition and add logical drives to it.  So if your master is currently 3 primary partitions, you should be able to delete the 25G and add a system partition and a swap partition.  But if you want to add two system partitions as I suggested, you may need to delete the existing partitions and start from scratch (obviously move your data off it first).  Tell me if that's not clear.

---

### Post by kag on 2007-02-12
Thanks, that seems pretty straightforward. I'll leave feedback as soon as I complete the switch (probably this weekend).

---

### Post by housam on 2007-02-13
I'll suggest that you free the slave drive F and to repartition it beside leaving drive C as it is to have a dual boot ( windows / ubuntu ) just till you get your ubuntu completely functionable.
Divide drive F to three partitions using Gparted ( a partitioning tool on the ubuntu live CD ) : one for the root ( / ) 10 Gb ext3 format, one for the swap ( swap format ) 1 Gb and the third is the rest for /home partition ext3 format. then go for the installation and when it comes to partitioning select the manual way.
You need [this guide ]("http://www.users.bigpond.net.au/hermanzone/")to make the dual boot installation.
You need [this driver ]("http://www.fs-driver.org/")to read ubuntu files through windows.
You need [this guide ]("http://www.psychocats.net/ubuntu/mountwindows")to mount windows partitions so you can read/write to it.

---

### Post by kag on 2007-02-14
Everything worked out fine. Here's what I did:

1. I used Partition Magic in Windows to convert my D: and E: drives to FAT32.
2. I left my F: drive in NTFS because I currently have some files bigger than 4GB (limit of FAT32). Will do the conversion later.
3. I installed Ubuntu and I chose the manual partitionning option. I destroyed my C: drive and created a 22GB ext3 partition for "/" and a 3GB swap partition in that space.

Voilà, everything works as expected. Thanks!

---

### Post by Skywalka443 on 2007-02-14
I have a similar problem, I have windows xp already installed on my laptop. I would like to keep it there and also install ubuntu with the dual boot and have the files i already have to be shared by windows and linux. I looked at the guide that someone posted in this thread and I was wondering if it was for computers with windows already installed or for fresh computers. Also would i need to move my data to the fat 32 partiton or could i keep everyhing on my current windows partition and just allow them to share that?

Thanks

---

### Post by IgnorantGuru on 2007-02-15
Skywalka443,

What guide are you referring to?

It depends on whether your windows install is all on one partition.  In that case you'll need to resize it (either using Partition Magic in Windows or GParted in linux).  Then you create the additional partitions for linux in the freed space.

If your Windows partition is NTFS, Ubuntu will read it but will not be able to write to it without additional drivers.  If it's FAT32, linux can read/write it.

Windows will not natively access linux partitions without additional drivers.  If you want to share data, usually it's best to create an additional partition for that purpose and make it FAT32.

My partitioning suggestions are here...
[http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017](http://www.ubuntuforums.org/showthread.php?p=2148017#post2148017)

---

### Post by Skywalka443 on 2007-02-15
the guide you posted earlier in the thread. I have all my data on my windows partition, I did however reseize it, I gave linux plenty of room (around 20 gigs) but i forgot about swap partition. So i am going to reboot the live cd and partition for swap and leave some free space for wahtever. I think your suggestions on partitioning cleared up the problem. However will grub auto install if i am installing with the live cd.

---

### Post by IgnorantGuru on 2007-02-15
yeah the installer should give you the option to install grub

---

### Post by Skywalka443 on 2007-02-15
done, im on ubuntu now.  Im also gonna install Kubuntu  just for the hell of it. Thanks for the help tho

---

