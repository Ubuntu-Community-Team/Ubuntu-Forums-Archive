---
title: "Partitions images and Resizing"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by samathyr on 2008-08-26
Hi Everybody!

I have some doubts about what I am about to do, and since is extremely risky, I would like to have your approval and some feedback. I have been using ubuntu as a primary OS since the release of Hardy. 

So.... 

My laptop is a **HP Pavilion dv6000** with roughly 112 Gb HD sliced in the following way.
sda1 (ntfs) 36 Gb (here I have windows vista, just in case, backups and some software that I need)
sda2 (ntfs) 5 Gb (this is the HP_Recovery partition, by default)
sda3 (linux-swap) 2 Gb (My SWAP)
sda4 (ext3fs) 68 Gb (My Ubuntu)

The dual-boot is achieved through GRUB
All these partitions are primary, no extended. The limit is 4. And what I want to do is the following thing:

Split sda4 in two partitions, and the new one acting as a /home (but not a real /home, just as a storage for films and music using ext3)

My first doubt! Can I remove the HP_Recovery without any risk? I dont need any Windows Vista recovery. If I do, and I create a partition ext3 for store all the films and songs I guess that I have to move the SWAP and Ubuntu partition first in order to occupy the free clusters left by HP_Recovery, is it dangerous? can my Ubuntu get unbootable?

I would like to make a image of my current Ubuntu and put it in the Windows Partition, but I don't know how to do it. I am using PartImage for this purpose, I have tried from the UBUNTU, but because sda4 is mounted I have tried also with the LIVECD, but I got some kind of problem:

My main problem is that I dont know what to put in Image File to Create/Restore in order to get the ISO in my Windows partition: 
[http://www.psychocats.net/ubuntu/images/partimage12.png](http://www.psychocats.net/ubuntu/images/partimage12.png)

How should I do it exactly?

I can use the Gparted live CD to resize and do everything, but I have to know about these things before gamble.

If I can't remove the HP_Recovery for whatever reason, how should I do the partitioning in order to fit 5 partitions without risks?

Thank you!

edit:
Would you recommend to resize the windows ntfs partition so I can use it as a storage partition fully accesable from both?
Would anything before explained affect GRUB?

---

### Post by louieb on 2008-08-26
I think this is what I would do.

[LIST]
[*]Use GParted to shrink your Ubuntu partition. (remember how large it is after being shrunk)
[*]Use partimage to backup your Ubuntu partition (get a [SystemRescue  Cd]("http://www.sysresccd.org/Main_Page") and look at this [Howto: Backup with Partimage - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=287522") )
[*]Back to GParted
[LIST]
[*]Delete your Ubuntu partition.
[*]Create an extended partition using all the now unallocated space.
[*]Create logical partitions inside the extended partition for /, /home, swap and a partition for your data.
[LIST]
[*]Note: the partition you create for / (root) must be the same size or larger that the partition you backed up.
[/LIST]
 
[/LIST]
 
[*]Restore your root partition from the partimage backup.
[*]Grub won't work need to fix that. [IDBS Restore Grub w/LiveCD]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD")
[*]Windows should boot thought GRUB. - still have some work to get Ubuntu to boot. Need the live CD again.
[LIST]
[*]need the UUID of your new partitions (run the **blkid** command)
[*]/boot/grub/menu.lst will have to be fixed the UUID of the / root partion will need to be changed to the new UUID. Also the GRUB root will have changed - Yours is probably (hd0,3) right now. That will change to what I don't know until you know the name of the new Ubuntu / (root) ie sda5? sda6?
[*]/etc/fstab will need to have the UUID of / (root) and swap updated with values from the blkid command.
[/LIST]
[/LIST]

Kind of a pain but thats what happens. Before you start think I would have a [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/") and a  [SystemRescueCd]("http://www.sysresccd.org/Main_Page") handy.

---

### Post by samathyr on 2008-08-27
Too complicated. What I can do is just resize the windows ntfs partition so I can use it as a storage partition. Is there any problem? Speed issues?

---

### Post by aitjcize on 2008-08-27
I don't think resizing your disk will make your ubuntu or M$ unbootable. Just use Gparted to resize it and don't worry about it at all
And because you HP recovery is in sda2, remove it won't cause any problem.
By the way, there is a free software for cloning you disk into image called Clonezilla.

[http://www.clonezilla.org/](http://www.clonezilla.org/)

it's totally free and under GPL

Create a Live CD or Live USB and Clone your disk!!

P.S. Technically, it won't affect GRUB. But if it did, just use ubuntu Live CD to fix it.
And I recommand you to create a vfat partition instead of a ntfs one, although ntfs can be mount on linux using ntfs-3g, vfat is more stable.

Hope it helps.

---

### Post by louieb on 2008-08-27
To add a 5th storage partition. You will need to remove one of your primary partitions and replace it with an extended partition. Then you can add 1 or 2 or more logical partitions inside the extended partition. 

Random thoughts: 

I suppose you could create a recovery DVD set and get rid of the recovery partition then  shrink the vista partition. vista has its own partitioner - it would be safer to use it rather that GParted. 
I'm 3 out of 4  on shrinking a windows XP partition w/out problems. 3 went fine. The other one well - after trying to fix it finally wound up doing a reinstall. 

I think a data partition should be formated with a file system native to the OS that will use it the most NTFS for windows, ext3 for Linux. I don't use vfat for anything except USB sticks.

Sounds like the data on this drive is important to you. Really think I would get my hands on an external drive and get it backed up before making any changes. Clonezilla is a good option for taking a snapshot of the drive.

Good Luck.

---

### Post by samathyr on 2008-08-27
The point is that the recovery partition is a Primary Partition, if I get rid of it, I will have room to create another ext3 primary partition.

But what I would do is just resize:
Approx.

now
Ubuntu 70 Gb
Windows 30 Gb

after
Ubuntu 30 Gb
Windows 70 Gb

I dont use Windows at all, if I get rid of my recovery partition, It will not worry me, I use it because of a university software uses a platform that requires Excel and Windows, but all the data is entirely online. If something happened I would install an XP instead, I don't need to recover anything.

In other words, the Windows Partition would be an Storage Partition (but with a bootable OS in there just in case) Also, I would use it to store all the backups before moving them to a DVD (that's why I want to shrink ubuntu partition, so I can image it quicker and easier)

The data is not that important as I use SD Cards for virtually everything. Customer Databases, University handouts, and so on are not inside the hard disk. But the amount of hours dedicated to customize and set up all the hardware are countless... for instance my broadcom wireless 

So... yeah I will do that, NTFS storage

---

