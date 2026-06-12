---
title: "Installation Problems on Dell XPS 15"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by Rachel_Bunker on 2013-11-25
I just received a new laptop (a Dell XPS 15 L521X) as a holiday gift.  It is currently running Windows 7.  I want to get rid of Windows completely and put Ubuntu 10.10 on it.  So I went ahead an made a live DVD to install it.  The installation problems begin before installation technically begins!  By that I mean that when you get to the part about selecting a partition to install on, the list is completely empty!  I mean, I don't even have the option to choose to install along side Windows or replace Windows completely!  Any advice would be greatly appreciated!

---

### Post by varunendra on 2013-11-26
First of all, Ubuntu 10.10 is way outdated now. It has reached its EOL ([End Of Life]("https://wiki.ubuntu.com/Releases")) in April 2012, which means it is no more supported since then and packages haven't been updated after that.

Secondly, you shouldn't remove windows until you are sure you are comfortable enough with Ubuntu. Even in that case, I would strongly recommend to create a set of backup DVDs before completely removing it. Just in case you need it back for any reason, besides, you (or the person who purchased it) have actually paid for it. :)

I would strongly suggest to download a fresh ISO of the latest LTS version of Ubuntu, that is, Ubuntu 12.04.3, via torrent to ensure the integrity of the ISO and a faster download : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads) (64 bit is strongly recommended).

Create a live USB or burn a CD from the downloaded ISO, and test it in Live mode first ("Try without installation" option in the live session). If it works fine in the live mode, proceed to installation.

If it fails to recognize the partitions as well, open a terminal (Ctrl-Alt-T) in the live session, and post back the output of -
```
sudo parted -l
```

---

### Post by fantab on 2013-11-26
> **varunendra said:**
> First of all, Ubuntu 10.10 is way outdated now. It has reached its EOL ([End Of Life]("https://wiki.ubuntu.com/Releases")) in April 2012, which means it is no more supported since then and packages haven't been updated after that.

Secondly, you shouldn't remove windows until you are sure you are comfortable enough with Ubuntu. Even in that case, I would strongly recommend to create a set of backup DVDs before completely removing it. Just in case you need it back for any reason, besides, you (or the person who purchased it) have actually paid for it. :)


+1.

Dual-boot Windows and Ubuntu. If you don't like Windows then don't use it but keep it. Apart from backup DVDs also create a Windows '[System Repair Disc']("http://www.sevenforums.com/tutorials/2083-system-repair-disc-create.html"), it will come in handy.

Download the latest version of Ubuntu which is 13.10, and install it. 
A new LTS [Long Term Support, with 5yrs. support] will release in April/May 2014. Then you can install that. No point in installaing 12.04.3 when you are only a few months from next LTS release. 
Ubunu releases a LTS version every two years. 

Once your Ubuntu DVD/USB is ready, post the output of 'sudo parted -l' as requested. And we can guide you on how to proceed further with Dual-booting Windows and Ubuntu.

---

### Post by varunendra on 2013-11-26
If multiple 700+ MB downloads aren't a problem, it is probably best to try both 13.10 and 12.04.3, and install whichever seems to perform better.

I personally believe there is always point in installing an LTS when it is going to be supported longer than the "currently available" next option. The point becomes stronger when it also supports the latest "[Hardware Enablement Stack]("https://wiki.ubuntu.com/Kernel/LTSEnablementStack")", which means apart from the interface, almost everything else becomes the same as the version whose kernel and xorg package versions are included.

We should remember that latest is not always the greatest, and liking/disliking the interface differences is a _very_ subjective matter. :)

I've also seen that LTS to LTS transitions are usually smoother. Although there is no guarantee that either of the transitions (LTS --> LTS or Interim --> LTS)  will be smoother than the other.

Not advocating the current LTS, just pointing out that before deciding to support LTS releases for 5 years, canonical has made sure that there does exist 'some point' in using it during its lifetime. :P

---

### Post by Rachel_Bunker on 2013-11-26
First, I want to appologize for not responding to this thread sooner; my husband has some medical problems and I was at the doctor with him.  Also, I again want to appologize for making myself seem like more of an idiot than I am because of typos and leaving out some pertinent information.  10.10 is a typo.  I meant to say that I'm trying to install 13.10.  The perinent information that I left out is that my old laptop, a 4 year old HP Pavilion DV7T, has been running solely Ubuntu for a few months now so I know that I want to run it.  I'm not the best at the command line but I"m learning!

As far as backing up Windows goes, I have a Windows 7 Professional disk that I got with the HP so I'm all set with that.  Also, the new computer came with a drivers disk so I'm all set with that.

Back to my installation problems.  I used the suggestion of sudo parted -l and here is what I got:

Model: ATA Hitachi HTS72755 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  41.1MB  41.1MB  primary  fat16        diag
 2      41.9MB  13.2GB  13.2GB  primary  ntfs         boot
 3      13.2GB  500GB   487GB   primary  ntfs


Model: ATA SAMSUNG SSD PM83 (scsi)
Disk /dev/sdb: 32.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  8589MB  8588MB  primary


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by fantab on 2013-11-26
If the SSD came pre-loaded with the laptop, then there is a possiblity that you have [Intel SRT]("http://www.intel.com/p/en_US/support/highlights/sftwr-prod/imsm"). You have to **[disable Intel SRT]("http://superuser.com/questions/476777/properly-disabling-intel-srt")**. Ubuntu won't install with it enabled. (It seems to do now, but I am not certain, remove it anyways Linux doesn't need it so much).
The following describes the steps involved.
[URL="http://ubuntuforums.org/showthread.php?t=2060108"]http://ubuntuforums.org/showthread.php?t=2060108 
[/URL]
And set the SATA mode in your BIOS to 'AHCI'. Confirm if you have this.
After this you can erase the SSD and HDD (if you don't want the pre-installed OS), reformat and Install Ubuntu. Install Ubuntu to SSD and use HDD for DATA.

If I were you, I would Install Ubuntu on SSD, leave Windows as it is. However I would [SHRINK Windows 7 partition]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html") (487Gb)  to create space for Ubuntu data.
Windows with Hibernation files won't allow you to shrink that partition beyond a point (we'd like to shrink it to about 70-100GB), you'll have to disable Hibernate function. Then Shrink.
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html)

Good Luck...

---

### Post by Rachel_Bunker on 2013-11-26
> **fantab said:**
> If the SSD came pre-loaded with the laptop, then there is a possiblity that you have [Intel SRT]("http://www.intel.com/p/en_US/support/highlights/sftwr-prod/imsm"). You have to **[disable Intel SRT]("http://superuser.com/questions/476777/properly-disabling-intel-srt")**. Ubuntu won't install with it enabled. (It seems to do now, but I am not certain, remove it anyways Linux doesn't need it so much).
The following describes the steps involved.
[URL="http://ubuntuforums.org/showthread.php?t=2060108"]http://ubuntuforums.org/showthread.php?t=2060108 
[/URL]
And set the SATA mode in your BIOS to 'AHCI'. Confirm if you have this.
After this you can erase the SSD and HDD (if you don't want the pre-installed OS), reformat and Install Ubuntu. Install Ubuntu to SSD and use HDD for DATA.

If I were you, I would Install Ubuntu on SSD, leave Windows as it is. However I would [SHRINK Windows 7 partition]("http://www.sevenforums.com/tutorials/2672-partition-volume-shrink.html") (487Gb)  to create space for Ubuntu data.
Windows with Hibernation files won't allow you to shrink that partition beyond a point (we'd like to shrink it to about 70-100GB), you'll have to disable Hibernate function. Then Shrink.
[http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html](http://www.sevenforums.com/tutorials/819-hibernate-enable-disable.html)
[http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html](http://www.sevenforums.com/tutorials/2672-partition-volume-shrink-17.html)

Good Luck...

Thank you so much!  I have decided to take your advice and keep Windows (shrinking the partition) and installing Ubuntu on the SSD.  Anyway, I have followed all the steps for shrinking partitions and stuff, and now I am ready to install.  My next issue is about partitioning the SSD.  How big of a swap partition should I make?

---

### Post by fantab on 2013-11-26
About 2-4 Gb shoud be fine. However, if you hibernate the computer with Ubuntu then the SWAP size should be equal to or more than your RAM Size in GiB (not GB). Ubuntu at present has some issues with Hibernate, so it is disabled by default. Also you can put your SWAP partition on HDD, if you want.

Your SSD is 32GB so:
28GB Primary Ext4 '/' ubuntu (I use 20GB '/' partition and after installing all I need, the total installed Ubuntu size does not reach 15Gb... so 28Gb is plenty)
4GB Primary SWAP.

How about Intel SRT? Do you have it?

---

### Post by Rachel_Bunker on 2013-11-27
Yeah, I have Intel SRT, but I disabled it

---

### Post by oldfred on 2013-11-27
You also have to remove the RAID meta-data from the drives.

This user re-enabled SRT with Ubuntu on hard drive, but some have installed to SSD.
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

If you have 4GB or more of RAM, you will rarely use swap. Swap on SSD might be a bit faster but if never used it does not really matter if on SSD or on hard drive.

I have a 64GB SSD and installed with two / partitions, one current install and one test/future install. My main working install uses about 10GB and I leave /home inside / (root) and have data partitions on rotating drives. I then link data folders back into /home so I have the same folders (plus a few) like Music, Video etc, but they really are on hard drive.

---

### Post by Rachel_Bunker on 2013-11-27
Yeah, I already disabled RAID.

I installed Ubuntu successfully on the SSD.  I do, however, have one last question.  How do I use the remaining space on the HDD for Ubuntu?

---

### Post by oldfred on 2013-11-27
Use Windows to shrink the Windows c: drive. You can then create a shared data NTFS partition. 
Did you put /home on the hard drive already? Or have you just installed to SSD and that is both / & /home.
That will work ok for a while but if you use Ubuntu a lot you will run out of room unless you move data to hard drive.

I have two data partitions, one NTFS from when I still used XP and one Linux formatted where all new data goes for sharing with all my Linux installs.

You then need to create partition(s), create mount points for each partition and add entries to fstab to auto mount those partitions. If Linux formatted you will also have to set ownership & permissions with chown and chmod. If NTFS settings in fstab totally control ownership & permissions.

       Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[URL="https://help.ubuntu.com/community/Fstab"]https://help.ubuntu.com/community/Fstab

      [/URL]
 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

    [URL="https://help.ubuntu.com/community/Fstab"]
[/URL]

---

### Post by fantab on 2013-11-27
> **Rachel_Bunker said:**
> I installed Ubuntu successfully on the SSD.  I do, however, have one last question.  How do I use the remaining space on the HDD for Ubuntu?

Have a small NTFS partition about 50GB or less so that you have some space to store Windows only files, also this partition can be used  to Share files/data between Windows and Ubuntu. This might come in handy.
The rest of the space can be formatted as Ext4 for Linux.

What oldfred suggests above is an excellent option to manage partitions. 

However, I do things differently with my Linux partition and NTFS partition. I don't use /etc/fstab. I don't automount my data partitions, meaning my data partitons (both, NTFS and EXT4) are NOT ready when Ubuntu starts.
My take is I don't 'always' use my data partition. I only need it when I am either reading a file from it or saving a file on it. For instance take a .mp3 music file. I am not listening to music all the time nor I am saving music to the data partition all the time. So why keep it mounted all the time? When I want to, listen to my music, I open nautilus/file-browser, from under 'Devices' click on the data partition it is mounted and opened at the same time, select my music and play it. In other words, its ready for use with one click. 

Likewise, when I want to save any data I mount the data partition and save data to it. Additionally, I change/set the default save path in individual applications to save files in data partition. For instance, I change the default save path in Firefox to save Downloads to the data partition. I change the default save path in LibreOffice Writer to save my documents to the data partition. 
(By default all application's save path is set to */home/user/Documents or Downloads or Pictures etc*. I change this to */media/user/Data Partition/Mydocuments or Mydownloads or Mypictures*).

Rarely, but when I forget to mount my data partition before saving any file to it, I get a error that such and such partition or file path does not exist as a reminder to tell me that I have forgot to mount my data partition. I mount it and the file is saved.
By the way, all partitions are listed on the launcher as well. I remove all the listed partitions from launcher but the data partitions, so I can mount it from the launcher, without having to open the file-browser/Nautilus.

You are free to follow either method. What oldfred suggests is the best way, according to the majority opinion. 

Good Luck...

---

### Post by oldfred on 2013-11-27
I do have other partitions that I do not mount like my /backup and older installs that may have something I want. So like fantab I do not mount those in fstab. I do label all my partitions so in Nautilus' left panel they mount with my label, not just a size or UUID.

I try to remember to label when I create new partitions with gparted, but often forget and then I use Disks or new systems it is now Disk Utility. Disks can do more things but some early versions had issues with gpt which I now use more. You can also label with terminal commands.

---

### Post by Rachel_Bunker on 2013-11-28
Thank you so much for all of your replies!  I'm now going to mark this thread as solved.  Happy Thanksgiving!!!

---

