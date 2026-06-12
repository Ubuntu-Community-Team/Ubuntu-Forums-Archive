---
title: "Installed OS on separate SSD"
date: 2013-04-07
forum: Installation &amp; Upgrades
---

### Post by mortenghaug on 2013-04-07
So I've got a laptop that came with Windows 8 installed on a small separate SSD and everything else went to a larger HDD. When I replaced Windows with Ubuntu I chose to install the OS on the small SSD and thought no more of it before I started installing all my programs etc. 

I now have serious space issues as everything automatically got stored on this very small SSD instead of the large HDD that I intended to use for everything but the system files. Is there an easy way for me to move everything except the essential system files to the large drive safely? And how do I change it so that this large drive is the default location for all files?

PS: I see that the HDD drive has remained untouched since the change to Ubuntu, everything on that drive is exactly as it were. As far as I know there is nothing on it that I need anymore since all the Ubuntu stuff has been stored on the small drive.

---

### Post by carl4926 on 2013-04-07
Question is
Are you using a separate /home? It's not the default in Ubuntu. But you really should have done that.

---

### Post by mortenghaug on 2013-04-07
i'm afraid my home folder is on the small drive, unfortunately. how can i move my home folder to the larger drive safely? i assume simply dragging and dropping won't do?

---

### Post by carl4926 on 2013-04-07
Back up the contents of your files in ubuntu  - and then do a clean install is what I would do. Only the OS has to be on the SSD. The OS being / or root  -  Be sure to use the same username with the new /home to avoid any ownership issues

---

### Post by darkod on 2013-04-07
There is a way to move /home to the hdd but it's your choice whether backing up the data and doing a clean install is easier, or trying to move the partition.

If doing the clean install don't forget you need to use the Something Else option and set the partition on the hdd to be used as ext4 with mount point /home.

If you want to try and move, so that you don't have to configure your system again (if you have already done system configuration and program installations), post the output of these commands and we can give you further instructions:
```
df -h
sudo parted -l
sudo blkid
```

---

### Post by carl4926 on 2013-04-07
@darko means
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)

---

### Post by oldfred on 2013-04-07
Good advice from Darko & carl.

Are you sure Windows was on SSD and not just a cache to make Windows boot faster. Ultrabooks use Intel SRT to cache Windows on a small SSD to speed Windows up.
How large is SSD?
I have my full install including /home in 27GB on my SSD, and use about 9GB. But all my data is on my hard drives and data folders like Documents, Music, Videos, etc all linked back to my /home. 

General instructions on moving /home.
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But if your Windows is on your Hard drive, does it still boot? And is Linux install UEFI or BIOS based?
Commands posted by Darko will help us see how system is configured.

---

### Post by mortenghaug on 2013-04-07
> **oldfred said:**
> Good advice from Darko & carl.

Are you sure Windows was on SSD and not just a cache to make Windows boot faster. Ultrabooks use Intel SRT to cache Windows on a small SSD to speed Windows up.
How large is SSD?

.......

But if your Windows is on your Hard drive, does it still boot? And is Linux install UEFI or BIOS based?
Commands posted by Darko will help us see how system is configured.

To be honest now that you mention it I am not 100% certain that Windows was on the SSD, might have been the way you said. The SSD is 16GB I believe. 

When I restart the computer I do get a selection menu where I can select Windows recovery or something like that, it doesn't go straight into Ubuntu. 

The way I installed it was UEFI i think, had to go into bios and Enable that and disable fast boot as far as I can remember. Then used Ubuntu from USB using Universal USB Installer. Selected the smaller disk as the install location.

---

### Post by mortenghaug on 2013-04-07
> **darkod said:**
> 

If you want to try and move, so that you don't have to configure your  system again (if you have already done system configuration and program  installations), post the output of these commands and we can give you  further instructions:
```
df -h
sudo parted -l
sudo blkid
```


Did that. Now what? :)

terminal output:

[I]morten@MortenULTRA:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb2        11G  8.5G  1.8G  84% /
udev            1.9G  4.0K  1.9G   1% /dev
tmpfs           770M  900K  769M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  1.6M  1.9G   1% /run/shm
none            100M   68K  100M   1% /run/user
/dev/sdb1        94M  123K   94M   1% /boot/efi
/dev/sda2       444G  118G  327G  27% /media/morten/001AADA61AAD9964
/dev/sda1       100M   30M   71M  30% /media/morten/SYSTEM
morten@MortenULTRA:~$ sudo parted -l
[sudo] password for morten: 
Model: ATA Hitachi HTS54505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  106MB  105MB   primary  ntfs         boot
 2      106MB   477GB  477GB   primary  ntfs
 3      477GB   500GB  23.3GB  primary  ntfs         diag


Model: ATA SanDisk iSSD P4 (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  99.6MB  98.6MB  fat32                 boot
 2      99.6MB  11.8GB  11.7GB  ext4
 3      11.8GB  16.0GB  4185MB  linux-swap(v1)


morten@MortenULTRA:~$ sudo blkid
/dev/sda1: LABEL="SYSTEM" UUID="B62CF0272CEFE07B" TYPE="ntfs" 
/dev/sda2: UUID="001AADA61AAD9964" TYPE="ntfs" 
/dev/sda3: LABEL="SAMSUNG_REC" UUID="6E5AD79E5AD760FF" TYPE="ntfs" 
/dev/sdb1: UUID="CF69-1C9D" TYPE="vfat" 
/dev/sdb2: UUID="a62929c1-0acc-414e-bbee-81cf29d3e78a" TYPE="ext4" 
/dev/sdb3: UUID="1f9b7c95-0c3c-4f93-977a-9103dbab6eba" TYPE="swap" 
morten@MortenULTRA:~$ 
[/I]

---

### Post by darkod on 2013-04-07
First of all, you have no unallocated space on sda, which is the hdd. Where do you plan to create the /home partition? What size do you want it to have?

---

### Post by mortenghaug on 2013-04-07
well I was planning on using the small SSD for system only and my 500GB HDD for everything else, so the /home partition should be on that larger drive. Would like to keep some of that 500GB for a future windows partition if i want to dual boot (want to play some of my windows games etc.).

---

### Post by darkod on 2013-04-07
OK. But as it is you have no space on the hdd to use for a linux partitions. So, I suggest you create a new gpt table on it, create one ntfs partition with the size you want to put aside for windows in the future, and from the rest of the hdd create on ext4 partition. Post the blkid results again after creating it.

---

### Post by mortenghaug on 2013-04-07
I'm just gonna do a complete reinstall. I want to completely blank everything everywhere (old windows files, current ubuntu stuff et all) and start fresh. When I run the Ubuntu installer from my pendrive, what should I do from there? This partition thing is confusing me a bit, so much simpler when I just had a single HDD.

---

### Post by carl4926 on 2013-04-08
I partition everything first with Parted Magic (Gparted)

So for example: Given what you have said:

*Remembering that your OS is installed to a mount point /
Your personal files to a mount point /home
(Typically Ubuntu makes a folder /home in the tree of / ) But now we are going to separate them.

So the SSD is where you want /
So create a single ext4 partition on the SSD, well actually / only need be 20GB, some people might use up to 30GB if they use a huge number of applications.
If there is more room than that on the SSD just leave it unpartitioned for now.


On the other HDD. I suggest you make the whole HDD extended space, then all the partitions inside it will be logical
Create swap = to 2x RAM
The a ext4 which will be for /home (all your personal files, music etc) (I make mine about 100GB, but on some machines it's half that) (I then have other partitions for storage, several TB)
So you need to decide. I also have other OS's install side by ... etc...

Then during Ubuntu install you follow the screens I gave earlier to get to the advanced
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_advanced.png)

Then set the partitions accordingly for / and for /home
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png) (This is just an example)
Make sure grub is set to sda

---

### Post by darkod on 2013-04-08
> **carl4926 said:**
> 
On the other HDD. I suggest you make the whole HDD extended space, then all the partitions inside it will be logical
Create swap = to 2x RAM
The a ext4 which will be for /home (all your personal files, music etc) (I make mine about 100GB, but on some machines it's half that) (I then have other partitions for storage, several TB)
So you need to decide. I also have other OS's install side by ... etc...


To make things more complicated, I don't agree with this. :)

First, I see no point using logical partitions until you have used three primary.
Second, and more important, you said you have in plan maybe installing windows in the future. It will not install on logical partition, and making the whole hdd one big extended partition you will have only logical partitions on it.

Making partitions is easy, especially from live mode using Gparted.

First decide how you want to split the 500GB, how much for windows (in future) and how much for the /home (your personal files). Also take into account you will need a swap partition at the end of the hdd, include it in the calculation too. Then boot the computer in ubuntu live mode, open Gparted and on the hdd first delete all ntfs partitions (you said you don't need the data, right?).
Then create one single primary ntfs partition with the size you decided for windows.
From the rest of the space, create the big ext4 partition for /home, you can make it primary or logical, up to you it will work both ways.
Then from the small unallocated space left at the end, make the swap partition.
Click the green button to execute the changes.

Then switch to the ssd in Gparted and create a single ext4 partition on it, it's only 16GB so use all of it. Again click the green button.

When installing you will need to use the Something Else, and when the partitioning step comes select the ssd partition, click the Change button, change the Use As to ext4 and mount point to /.
Then select the /home partition, again the Use As is ext4, mount point /home.
Then select the swap partition, the Use As is swap area, there is no mount point to use for swap.
Leave the ntfs partition alone, you don't need to do anything about it.

For the bootloader destination select /dev/sdb, the ssd. No number in it, just /dev/sdb. And that's it.

In bios don't forget to make it boot from the ssd. If there is no such option, you will need to install the grub2 bootloader to the hdd, /dev/sda, instead of /dev/sdb.

---

### Post by carl4926 on 2013-04-08
> [COLOR=#000000]It will not install on logical partition[/COLOR]It should, I have done it. But it does need a suitable primary for it's boot code

But, yes, if you plan to install winders, then @Darko makes some valued points

---

### Post by darkod on 2013-04-08
> **carl4926 said:**
> It should, I have done it. But it does need a suitable primary for it's boot code


I know, but that still means you need a primary partition (big or small nevermind), on a disk where you will have only extended partition. I didn't want to complicate it further going into too much explanations. :)

The simple statement seems to be: windows can't install on logical (even when it's not 100% correct) :)

---

