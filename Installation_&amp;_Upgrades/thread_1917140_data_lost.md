---
title: "data lost"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by raspatan on 2012-01-29
Dear all,

Yesterday I decided to install Ubuntu on my laptop together with Microsoft. I have one HD of 120gb, partitioned into a small fat, a large 40 gb with windows on it, another 10gb that I created for Ubuntu (using partition magic), and another fat32 70gb where I store my parsonal data, music, works, etc etc.

I created the USB to install ubuntu 11.10, no drama. I selected the 10gb to install ubuntu on it (ntfs) and then it asked me to select a "swap" drive to run ubuntu faster or so. It was not compulsory but the way the message was written made me accept the option, so I chosed the 70gb one, thinking it would use the free space (40gb) on it for whatever it needs. Now, I cant find it on ubuntu. When I look at it using partition magic within windows, it says 70gb used and cannot do anything without it besides formating it. When I enter the installation menu again to try to "unswapit", it says 70gb free, 0 mb used. OMG.

Did I lose all my data? The bloody message asking me to give some free space did not tell me it would DELETE all the data on it. So please, I need help. I have a partial back-up of my data only. 
Furthermore, I tried to use a program called QTParted to see partitions within ubuntu but I don't know how to use it. Instuctions seems to be for advanced users ([http://qtparted.sourceforge.net/faq.en.html](http://qtparted.sourceforge.net/faq.en.html))  I'm rather new to linux and my previous experience with red-hat some years ago was very problematic. I hope this time will be better!
 
I hope anyone can help me! Tahnk you very very much in advance!!!

---

### Post by darkod on 2012-01-29
You should be able to bring the partition back with testdisk:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

There is a manual on their website too:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

First of all, do not boot from the HDD. Boot with the ubuntu usb stick in live mode, connect to the internet with a wired connection, download and run testdisk.

And next time DO NOT create partitions for ubuntu from windows, it doesn't install on NTFS. Leave the space as unpartitioned, it will create the partitions it needs into it (in this case two partitions).

Also, 10GB is a bit small for ubuntu, see if you can give it more if possible.

And you still keep your data on FAT32 partition? Why not NTFS?

---

### Post by ottosykora on 2012-01-29
>that I created for Ubuntu (using partition magic), <

hope your windows is XP and not Vista or w7.

 Partition magic will do lot of damage when all was set up with the 'vista' type of partitions and you go to change it with partition magic.

I would strongly recommend to use partition magic only on old computers with older operating system versions.

as far as QTparted, well you can use the gparted from within ubuntu, this works very similar way to partition magic, so you will find it more easy to use.

But this all will come into play when you did recover the partitions with testdisk as instructed.

---

### Post by recluce on 2012-01-29
> **raspatan said:**
> Dear all,

Yesterday I decided to install Ubuntu on my laptop together with Microsoft. I have one HD of 120gb, partitioned into a small fat, a large 40 gb with windows on it, another 10gb that I created for Ubuntu (using partition magic), and another fat32 70gb where I store my parsonal data, music, works, etc etc.

I created the USB to install ubuntu 11.10, no drama. I selected the 10gb to install ubuntu on it (ntfs) and then it asked me to select a "swap" drive to run ubuntu faster or so. It was not compulsory but the way the message was written made me accept the option, so I chosed the 70gb one, thinking it would use the free space (40gb) on it for whatever it needs. Now, I cant find it on ubuntu. When I look at it using partition magic within windows, it says 70gb used and cannot do anything without it besides formating it. When I enter the installation menu again to try to "unswapit", it says 70gb free, 0 mb used. OMG.

Did I lose all my data? The bloody message asking me to give some free space did not tell me it would DELETE all the data on it. So please, I need help. I have a partial back-up of my data only. 
Furthermore, I tried to use a program called QTParted to see partitions within ubuntu but I don't know how to use it. Instuctions seems to be for advanced users ([http://qtparted.sourceforge.net/faq.en.html](http://qtparted.sourceforge.net/faq.en.html))  I'm rather new to linux and my previous experience with red-hat some years ago was very problematic. I hope this time will be better!
 
I hope anyone can help me! Tahnk you very very much in advance!!!

You quite probably lost all or most of your data. Data recovery tools may be able to recover some files if the data was too fragmented. For FAT32, there are more recovery tools than anybody can shake a stick at. But I must admit: no backup, no sympathy from me.

---

### Post by darkod on 2012-01-29
> **recluce said:**
> You quite probably lost all or most of your data. Data recovery tools may be able to recover some files if the data was too fragmented. For FAT32, there are more recovery tools than anybody can shake a stick at. But I must admit: no backup, no sympathy from me.

Just to note that I wouldn't agree it's that hopeless. The partition type is just changed and testdisk is very good changing it back. Because it was changed to swap most likely it was never even used unless you really needed to use the swap space. Which means little or no data is overwritten.

Although I have to agree on the no backup remark. Especially before doing an installation of an OS that you have little or no experience with.

Not to mention that the whole approach of creating a single ntfs partition for ubuntu was flawed from the start...

---

### Post by ottosykora on 2012-01-29
@recluce
yes, some time ago, there was a guy here, who somehow installed ubuntu on his windows partition completely.
The partition was formated to the linux file system and complete os installed.

After changing the partition back to windows format, the complete windows install came back with no data lost at all.

There is no magic behind it, provided the partition was big compared to data actually written to it, as windows uses the beginning of the partition and linux starts using the middle portion of it.

Recovery is therefore no hopeless, provided no unnecessary writes are applied to the partition.


BTW: here trhere was an other happy guy to recover formated partition
[http://ubuntuforums.org/showthread.php?t=1914776](http://ubuntuforums.org/showthread.php?t=1914776)

---

### Post by raspatan on 2012-01-30
Hi! Thank you all. 
Well, I tell you what I did because the problem is even worse now.
I downloaded the Testdrive software and tried to see how it works. Indeed, my partition is there, in the linux swap format. I created a backup (.idd file?) of the partition (70gb) just in case and saved it in an external HDD. Later, using the other application that comes within the software (picture recovery or something like that) I could see indeed that my data is there. That software let me recover jpg, mp3, doc, and etc etc. So, the data seems to be there as it may not be overwritten as some one suggested. (i didnt recovered it because having my backup idd file and knowing it was there, I was more calm.
Ok, then, I proceed to change the type of the disk back to HTS NTFS (or so, can't remember exactly) and then do the write thing process, asking me to restart.

So, once i restart, immediately after booting it appears: 
error in partition
grub rescue> and I have no idea what to do. I try to run ubuntu from my USB boot from which I initially installed and it doesnt work, either by running it or trying to install it again.

So in conclusion, my computer is useless now! Although I have the backup idd file, which is good, even though I have no idea how to use it.

Can you guide me know? I have no idea what to do and I don't want yet to take the extreme decision to reinstall windows XP (the one I have) formatting everything (I have data on C that I havent saved!).

Thank you very much in advance!!

---

### Post by darkod on 2012-01-30
In your first post you said the 70GB partition was FAT32, and then you say you restored it as NTFS (I think). Did testdisk discover it as FAT32, NTFS or both (it can suggest two partitions depending what existed on the disk earlier)?

You should always be able to boot the ubuntu usb in live mode, did you change anything on the stick? Try again. Don't try to install it, even if it succeeds it can't help much. Just try to load it in live mode.

---

### Post by raspatan on 2012-01-31
Well, to tel the truth, I wasn't sure whether the format was FAT32 or NTFS so, given your initial comment, I thought maybe it was NTFS, but I can see that it was not. I created another ubuntu boot disk, this time the ubuntu rescue remix (downloaded the iso, then put in a pendrive with ultimate something application). But it didn't work. It says mising config.c32 or something similar, and then the prompt "boot:". I'll do it again but I dont know what was the mistake. 

Remember that I turned the partition into a swap so Testdrive said it was a "Linux swap partition".

Thanks again!!

---

### Post by darkod on 2012-01-31
No, the point of testdisk is that it can find partitions that were deleted and reformatted. The quick search might say it's Linux Swap type, but the deeper search has to find it as FAT32 or NTFS, depending what it was.

You have to do a deeper search and see what it finds, then change the D for example, into P or * depending if it was bootable or not. Only then you write the new partition table.

If testdisk shows it only as Linux Swap even after the deeper search, it can't recover it.

EDIT: To elaborate further.
The quick search of testdisk would usually locate the partitions as they are, in most cases. So that is basically useless for recovering partitions.
But the deeper search is the powerful tool you need. It locates partitions existing earlier which is exactly what you need. For example, into the same locations on the disk, it can locate the linux swap and also the fat32. The choice will be up to you which one to mark as not needed (the letter D for Deleted), and which one to mark with P for primary, L for logical, or * for primary bootable.

---

### Post by raspatan on 2012-02-01
Thanks Darkod, but the problem is before that. I cannot enter into ubuntu or windows and do that since I have boot problems now (the grub rescue promnt at the beggining). 

I created twice the ubuntu rescue remix ([http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)) just like it says, using a pendrive, but when running it it says "error, cant find the vesamenu.c32", and then a "boot:" prompt appears.

I will create a CD now with the same rescue remix to see if the problem is the pendrive....

Otherwise, I think i will have to have a bootable ubuntu on a cd and get testdrive working on it from a pendrive and then try to change the disk type back to FAT32... do you think this is a possible solution? 

Thank you very much!!!

PS: do you know how do I use the .dd backup image that I created from the 70gb partition?

---

### Post by darkod on 2012-02-01
I thought you are using the ubuntu cd to boot into live mode this whole time. Doesn't matter if the hdd is unbootable, that's what we are trying to fix.

You should use ubuntu live mode and testdisk so that the hdd is not in use during the operation. Wired internet should work in live mode so you can download testdisk directly into it.

---

### Post by raspatan on 2012-02-01
Hi! Finally I could run ubuntu live cd and testdisk! 

So, first, I changed the partition back to FAT32 (from HPFS-NTFS, which I changed initially and let my computer scrued up), then I did the write process and rebooted, but again the grub rescue prompt came out. So, I did the deeper search as you suggested me. Here is the output:

```

Disk /dev/sda - 120 GB / 111 GiB - CHS 14594 255 63
     Partition               Start        End    Size in sectors
>* FAT16 >32M               0   1  1     8 254 63     144522 [DellUtility]
 **D HPFS - NTFS **             9   0  1  3943 254 63   63215775   (has files, my C drive)
 D HPFS - NTFS              9   0  1  5279 254 63   84678615     (has files, my C drive)
 D HPFS - NTFS              9  13  5  1314 119 21   20971520    (damaged)
 D HPFS - NTFS           1314 119 22 14266 198 12  208078848    (damaged)
 **D Linux**                 3944  10 35  5279 236 13   21460992       (has files, ubuntu)
 D Linux                 4483   9  7  5818 234 48   21460992         (damaged)
 D Linux                 4490  12  3  5825 237 44   21460992         (damaged)
 D Linux                 4493  27 15  5828 252 56   21460992        (damaged)
 D Linux                 4495 232 26  5831 203  4   21460992        (damaged)
 D Linux                 4496 237 30  5832 208  8   21460992        (damaged)
** D Linux Swap**            5280   1  1 14592 254 45  149613264    (no files option available)

 
```

damaged NTFS says: NTFS found using backup sector!
damaged Linux says: EXT4 Large file Sparse superblock Recover

Then I changed the bold ones to P, L and L respectively. Also I changed back the linux swap partition to Linux Swap....the result...let me tell you after rebooting!

---

### Post by raspatan on 2012-02-01
So, it seems the partitions are fine now. Analysis result and quick search match (I setted two primaries and one logical later so now it seems fine). It seems the partition with my data is a swap partition anyway. I created a .dd file and i will try to see whether I can recover the data from it.

Now I installed the grub. Below you can see my code and the result. I will reboot now and se how it goes....

ubuntu@ubuntu:~$ sudo grub-install --boot-directory=/media/564d5bf7-c30b-4417-af2c-b1df694de061 /dev/sda
/usr/sbin/grub-setup: warn: Sector 32 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
/usr/sbin/grub-setup: warn: Sector 33 is already in use by FlexNet; avoiding it.  This software may cause boot or other problems in future.  Please ask its authors not to store data in the boot track.
Installation finished. No error reported.

---

### Post by raspatan on 2012-02-01
omg, this has no end!!!!

so now there isa grub installed, but it just leads me to a grub> prompt, with many commands available but no idea wha to do. Boot command doesnt work. Is the grub not configurated? Should it recognize both Win Xp and Ubuntu? How can I get the inicial start up that I had when i installed ubuntu for first time when it showed me ubuntu, safe mode, dell partition and win xp?

Thank you very much!!

---

### Post by ottosykora on 2012-02-02
try:

[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)


but before you use any grub repair, write down exactly where you want have it.

But it looks that the grub works itself, but just can not find the kernel to boot or so.

---

### Post by darkod on 2012-02-02
That result of the deeper search unfortunately shows the 75GB partition only as Linux Swap. No other options.
Maybe writing the partition table mixed it up, or it was not recoverable from the start. The testdisk instructions were very clear not to write any partition table until you see all your partitions detected.

Even if you get it to boot (repair the grub error) it looks to me like the 75GB partition will be only a swap partition, and not what you wanted to recover.

---

### Post by raspatan on 2012-02-02
Hi! Finally my boot is working! I used Boot-repair! Amazing!!

Now, im trying to open the .dd file but it just tells me the file is a linux swap partition. So the only way to recover the data is using the Photorec, but the problem is that It gives me the data with random names so basically i will have to rewrite all name!! 

It is very bad but at least i will have most of my data, hoping that ubuntu didn't overwrote some of them.

Well, after all this, I will still give ubuntu a try, but I will reinstall it again because Im using 70GB as swap!! 

How much space do you recomend me to give a swap partition? and ubuntu itself? I want to have a partition without any OS to share data between windows and ubuntu. 

Thank you all for the help!!!!!!
Best!!

---

### Post by darkod on 2012-02-02
If you share the most important data, including videos, photos, etc, ubuntu doesn't need much space.
For the system (root) partition, 15GB is more than enough. For swap, even 2GB is enough but if you plan to hibernate regularly then your swap partition needs to be at least 1.5 x RAM so that all of the data in the memory can be saved to the swap when going into hibernation.

Note that in this case your Home folder (similar to My Documents in windows) will be included in the root partition, so if you plan to keep any big files in ubuntu you will need to give it more than the 15GB mentioned above. How much is up to you.

---

