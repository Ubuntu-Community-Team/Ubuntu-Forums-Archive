---
title: "no idea how to partition correctly..."
date: 2013-08-04
forum: Installation &amp; Upgrades
---

### Post by jessica2 on 2013-08-04
I'm a complete noob. I want to install Ubuntu on my ASUS Zenbook UX31E but I don't know how to partition windows7/ubuntu...I have a 128gb ssd and 4gb ram. 

Say I won't be using Windows *that* often...only for Adobe work pretty much. Should I have three partitions? One for Windows, one for ubuntu, one for files? And what the heck is swap and root and home?!

I don't want to mess up.

Help!!

---

### Post by amra.sonntag2 on 2013-08-04
Having the three partitions you mentioned seems reasonable. Remember to make your data partition for files with the NTFS filesystem. That way you will be able to read it from both operating systems.

For your other question you need to understand the linux filesystem a little. But lets just say, that root ( / ) is the base of the file system. You can make one partition for root and your Ubuntu will work fine with that. In root you have the home folder ( /home ), where usally user data and settings are stored. It isn't a bad idea to create a partition for it, because than your data and settings are seperated from the main operating system. If you ever have to upgrade/reinstall, you will be able to do so on the root partition and keep your data and settings by reusing the /home partition in the new installation.

Linux uses a swap partition if your system runs out of RAM. How often it is used and how much swap you need depends on what you do with your machine. In case you want to use hibernate, you should however have as much swap as RAM, since hibernation writes your RAM onto the swap partition. Given that you "only" have 128 gb disc space, you might not want to create that big a swap partition.

---

### Post by Topsiho on 2013-08-04
First: you should create space for Ubuntu in Windows7, which I presume is installed already. If you do this outside of Windows7 (eg. with gparted) Windows will not recognize the new situation and probably won't boot next time.

Second: you should know that each harddisk can have only 4 primary partitions. If you need more, one primary partition should be sacrificed to become an extended partition, which is a container for as many logical partitions as you want.

You can create an amount of unallocated space, and let Ubuntu install into that unallocated space. Ubuntu will create a partition for /  (root partition), and swap into a logical partition. Not sure how Ubuntu will install into an unallocated space, next to three already used primary partitions.

I always install Ubuntu into three partitions: /  (root partition), for which 20 GB is more than large enough, swap (twice the RAM), and for the rest /home  (a separate home partition). / then will contain all system files, and /home all personal files.

Creating space in a Winows7 install is tricky, and I have never done this (never had Win7). You'll need advise from someone else.

ALWAYS FIRST BACKUP DATA YOU'D HATE TO LOSE

Topsiho

---

### Post by carl4926 on 2013-08-04
> **jessica2 said:**
> I'm a complete noob. I want to install Ubuntu on my ASUS Zenbook UX31E but I don't know how to partition windows7/ubuntu...I have a 128gb ssd and 4gb ram. 

Say I won't be using Windows *that* often...only for Adobe work pretty much. Should I have three partitions? One for Windows, one for ubuntu, one for files? And what the heck is swap and root and home?!

I don't want to mess up.

Help!!

Is this windows 8? [edit -sorry win 7, I missed that] so probably not efi
Check this [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

If you boot the ubuntu live cd/usb
Let us see

```
sudo parted -l
```

---

### Post by jessica2 on 2013-08-04
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA SanDisk SSD U100 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  119GB  119GB   primary  ntfs         boot
 2      119GB   128GB  8590MB  primary  fat32        hidden, lba


Model: SanDisk Cruzer (scsi)
Disk /dev/sdb: 4000MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      8192B  4000MB  4000MB  primary  fat32        boot



Here it is. So for Win7, I'll be doing Adobe work mainly. I'm planning to use Ubuntu for most of what I will do: developing, surfing, etcetc. I don't game. Can anyone tell me how I could best partition my system? I just want to get a feel of how many gigs I should assign to each partition.

---

### Post by jessica2 on 2013-08-04
And how would I backup data if I don't have a DVD/CD drive? (I've got an ASUS zenbook) Do I make an iso and a bootable USB or something like that?

---

### Post by carl4926 on 2013-08-04
> **jessica2 said:**
> And how would I backup data if I don't have a DVD/CD drive? (I've got an ASUS zenbook) Do I make an iso and a bootable USB or something like that?

Backup to an external USB device or multiple pendrives if necessary.

I'd use a Live USB of Parted Magic to create partitions - But I have to say, you'll not have masses of space because windows 7 need much of what you have. Decide what you can spare then defrag windows.
Now use Windows to shrink partition 2 and leave the space you free up unformatted.
Now use Parted Magic to create and extended partition to take up all the free space, then create a logical 2GB swap and finally a logical ext4 to use all the remaining space. Apply. 

Now install Ubuntu
[https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf](https://dl.dropboxusercontent.com/u/10573557/Ubuntu/13_04/13_04_slideshow.pdf)

---

### Post by jessica2 on 2013-08-04
Well how much will win7 need? Damn win7. :/ Would running adobe products in a virtual box instead be worth it? Or something like wineHQ? Or too laggy?

---

### Post by carl4926 on 2013-08-04
> **jessica2 said:**
> Well how much will win7 need? Damn win7. :/ Would running adobe products in a virtual box instead be worth it? Or something like wineHQ? Or too laggy?

I have win 7 in a 60GB partition and it's fine for me. But I never use it, but I do have a CS4 installed, L Office and general other stuff.
Virtual Box might be OK, but you need a copy of windows.
I've only got windows installed because I do home tuition. 
I personally never use it now.

---

### Post by fantab on 2013-08-05
Running Adobe with Wine works best with older editions of Adobe. You have check the WineHQ data base and check the rating to ascertain whether the version you have works or what adobe version works best.

Regarding Partitions: if you only want to use Windows for Adobe then about 30-35GB should be enough for Windows. If I were you I would:
35GB Primary NTFS for Windows
25GB Primary Ext4 '/' for Ubuntu
66GB Primary Ext4 '/home' for your personal DATA
2GB Extended Partition
2GB Logical SWAP

With 'msdos' partition table there is only 4 Primary Partitions Limit. To overcome this we need an Extended Partition which is a Primary Partition and also a container for Logical Partitions.

Also there are very good Linux alternatives to Adobe... check out [Ubuntu Studio]("http://ubuntustudio.org/") for more details. I used to use adobe but gradually I have switched to Linux alternatives.

My two cents...

---

### Post by Buntu Bunny on 2013-08-05
> **fantab said:**
> Also there are very good Linux alternatives to Adobe... check out [Ubuntu Studio]("http://ubuntustudio.org/") for more details. I used to use adobe but gradually I have switched to Linux alternatives.

That depends on what one wishes to do. AFAIK, only Adobe Distiller can create the PDF/X-1a:2001 files required by many professional printers such as Lightning Source.

---

