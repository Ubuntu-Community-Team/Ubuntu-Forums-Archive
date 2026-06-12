---
title: "best way to partition 250GB for dual boot windows xp and ubuntu"
date: 2011-06-02
forum: Installation &amp; Upgrades
---

### Post by adhamj90 on 2011-06-02
hey, 
i know there are lots of posts to talk about this but i'm still not sure about what to do :confused:. 
I have a new 250GB hard disk and want to use it to dual boot windows xp and ubuntu. 
i know i will have install xp first, but what would be they best way to partition the drive ? i want to be able to have some space in xp to to download and use 3d simulation programs and for gaming. and i also want to be able to see all my data from both OS.
I guess i'll have to choose the manually partition the drive option on the ubuntu installation, but then what should i do exactly? and what would the partition types be?  NTFS, FAT32, etc..
I have a 2GB RAM, i think it matters for the swap partition size.

thanks a lot in advance

---

### Post by mivadar on 2011-06-02
You probably want around 2 GB swap.

If You want to reliably read and write data files from both Linux and Windows, in spite of advances in mounting NTFS partitions in Linux and various ext4/reiserfs readers in Windows, Your best and most robust option is probably still to have a FAT32 partition.
Limitations of FAT32: partition can't be larger than 127.5 GiB (&#8776;137 GB), and individual files can't be larger than 4 GiB.
(With Your disk, the second is more important => e.g. FAT32 can't handle a DVD image of a full DVD.)

If You don't want full modification control over files in the shared partition, but just see them (i.e. read, not write), You don't have this problem - there is Windows software that can read and copy from Linux partitions, and ntfs reading is robust in Linux.

You probably want Your Windows partition to be larger than 30 GiB, or XP won't meaningfully run.
If You want to use games and 3D simulations, and actually store some files on the XP partition, not just dump them in the shared partition, probably over 50 GiB is better.

So, my suggestion would be:
1. Install Windows wiping the whole drive (250 GiB).
2. Run a defragmentation or two in Windows after install (makes the subsequent shrinking easier).
3. Install Ubuntu, do manual partitioning.
4. Shrink the Windows partition to 50-100 GiB, depending on Your estimated Windows usage.
5. Make a 2 GiB swap partition
6. Make a 20-40 GiB ext4 partition, mount it as '/' (this will be Your linux root - choose the size depending on what You want to use it for, and whether You plan to leave data files here or just in the shared.)
7. Make the rest a FAT32 partition, mount it as '/dos' (this will be Your data partition that both Linux and Windows can access without problems.)

Note, to be safe, don't make the FAT32 larger than 125 GiB.
If You want Your OS partitions (XP NTFS and linux ext4) to be lean, and You're not planning to dump files there ( => only in the shared partition, and You're not planning to have files larger than 4 GiB loitering on Your computer), You probably need to make  two FAT32 partitions.

So:
Configuration for a lot of shared space:
40 GiB NTFS (primary) (for XP)
2 GiB swap
20 GiB ext4 /
94 GiB FAT32 /dos1
94 GiB FAT32 /dos2

for decent shared space, more or less equal use of XP and linux:
75 GiB NTFS (primary) (for XP)
2 GiB swap
48 GiB ext4 /
125 GiB FAT32 /dos

for only reading, and using mostly Windows:
200 GiB NTFS (primary) (for XP)
2 GiB swap
48 GiB ext4 /

Windows won't run if XP is not installed in a primary partition (anyway, if You start with the XP installation and then shrink it, You don't need to worry). Linux will run from anywhere.

I think You get the idea :) - play around with the numbers.

---

### Post by shnplr on 2011-06-02
Hi,

A simple approach could be this, say with XP and Linux each taking 50%.

1. Install XP creating NTFS partition of 125G (leave remainder of disk unallocated/unpartitioned for linux)

2. Install Linux - choose the option to install alongside XP.  This will automatically put ubuntu on the remainder of the disk. It will create an extended partition with 2 logical partitions (/ ~120GB ext4 and swap ~2-4GB)

Your linux system will read/write the NTFS drive no problem
Your NT system WONT be able to read your linux system (ext4).

Assuming you really want a dual boot and not a virtual system, and you absolutely MUST have XP read your linux fs (without having to perform additional copy operations) then you could say manually partition and mount your /home on ext3 - but this is limiting a nd tying your linux install to windows. You'd also need to install additional windows software to read the ext3 partition.  Not my preference.

You can simply boot ubuntu and copy files manually onto the NTFS partition. Dont create any FAT32 partitions as that's redundant (i.e. why copy to FAT32 when you can copy to NTFS)

If you want to manually partition, create / on primary or extended (defaults to primary)
create all your other mount points in the extended parttion (default).  You only need / and swap as minimum.  

If you really want to you say / 50GB (primary - ext4),  swap 3GB (extended) and /home remained of disk space space (extended - ext3 or ext4)

Hope this helps

Cheers,
Paul

---

### Post by oldfred on 2011-06-02
I think the NTFS driver in Ubuntu is reliable enough for a shared NTFS data partition. I originally used FAT32 for this with my XP install with 6.06, but with 9.10 I converted to NTFS and have had no issues.

But I do not write into my XP install unless I have to make repairs from Linux. I do all reading & writing in the shared NTFS partition. I have my Firefox & Thunderbird profiles & all photos still in my shared partition and have had no issues. I now rarely boot XP and put most new data in a Linux partition, but still have my shared NTFS partition unchanged.

While I normally recommend a /home partition, if you are putting most data into the shared partition, then you can leave /home inside root and make root a little larger.

I generally like to keep system partitions smaller and have most data in data partitions. Easier to backup data and if you have to reinstall system, you do not have to reinstall data (but backups still required). Also smaller system partition has slight performance advantage as drive heads do not have to search a large partition for the most often used files.

---

### Post by underquark on 2011-06-02
I'd go for:
75GB Windows
48GB ubuntu
2GB swap
125GB shared data

If you don't have much shared data but lots of Windows games and stuff:

150GB Windows
48GB ubuntu
2GB swap
50GB shared data


Having said that, I'm running XP and ubuntu (did have 9.04, tried 11.04, settled on 10.04 for the time being) split about 50/50 on a 1TB drive.  I used to merrily dip in and out of the Windows partition and share data.  I now have a lot of data on an 1TB disc formatted as NTFS and continue to read and write to this from both OSs without mishap so far.  Risky - possibly.  Backups - definitely.

---

### Post by adhamj90 on 2011-06-08
Tank you all for the replys 
I got my new hard disk today 
Inatalled Windows 7 on the whole 250 GB
Now im trying to manually partition the drive 
I have sda1 of 100mb was created during the Windows installation. And the rest on sda2
So Im changing the sda 2 and created a 3gb partition as swap but it's taking too long to do it. It is still working. Is it normal? I clicked on he sda2 and then change and put 3000 mb. Is it the correct way to do it? 
Next shoul o put 75000 mb for ubuntu then another 100000 mb for the shared ? 
And do I have to change the mount point ? Please help me quickly as I'm doing the installation of ubuntu 10.10 now. Thanks a lot again

---

### Post by adhamj90 on 2011-06-08
Can I partition the hard disk from another place other than from
Inside the ununtu installation?? Maybe use the live session ? Or from
Inside windows. Because when partitioning the swap area. It deleted the whole thing including windows!!! 
What should I do exactly ?!!

---

### Post by oldfred on 2011-06-08
Use windows tools for windows and Linux tools for Linux.

You should use Windows 7's MMC to shrink windows. But windows does not see Linux partitions.

You should use a liveCD to use gparted or even download a gparted liveCD. If you have a swap partition you have to click on the swap and right click swap off as the liveCD will mount it to speed thing up.

If it was taking a long time was it because you were shrinking window from gparted?

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

---

### Post by adhamj90 on 2011-06-08
I'll do the easy way. Re install windows now because it has been delete it. But I'll install it only on half the drive. Then install ubuntu automatically. I don't want a shared space necuase I don't think I'll be needing it. Thanks

---

