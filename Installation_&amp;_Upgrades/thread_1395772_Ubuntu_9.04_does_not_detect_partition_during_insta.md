---
title: "Ubuntu 9.04 does not detect partition during installation"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by jocaps on 2010-02-01
I have seen this in many of the forum entry.. and each time a new poster writes "I have the same problem with *bla* specification" the admin interrupts and writes "Please start another thread..". So I will go one step ahead and start this thread.. I am no expert in harddisk partition, but I feel that this is just a partition orderig/size problem.. I have done the following using the livecd:

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8df58df5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20980889    10490413+   c  W95 FAT32 (LBA)
/dev/sda2        20980890   312576704   145797907+   5  Extended
/dev/sda3       209760705   308335544    49287420   83  Linux
/dev/sda5        20980953    83907494    31463271    7  HPFS/NTFS
/dev/sda6        83907558   146834099    31463271    7  HPFS/NTFS
/dev/sda7       146834163   209760704    31463271    7  HPFS/NTFS
/dev/sda8       308335608   312576704     2120548+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size= 20980827, Id= c, bootable
/dev/sda2 : start= 20980890, size=291595815, Id= 5
/dev/sda3 : start=209760705, size= 98574840, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0
/dev/sda5 : start= 20980953, size= 62926542, Id= 7
/dev/sda6 : start= 83907558, size= 62926542, Id= 7
/dev/sda7 : start=146834163, size= 62926542, Id= 7
/dev/sda8 : start=308335608, size=  4241097, Id=82
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=  3919797, Id= 6, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0
```

I wonder if this has to do with my extended logical partition. Someone who knows better could probably help me here. Thanks in advance.

---

### Post by darkod on 2010-02-01
Not sure what your problem is, because you didn't say (except the title), but this is very strange:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20980889    10490413+   c  W95 FAT32 (LBA)
/dev/sda2 [COLOR=Blue]20980890   312576704[/COLOR]   145797907+   5  Extended
/dev/sda3       [COLOR=Red]209760705   308335544[/COLOR]    49287420   83  Linux
/dev/sda5        20980953    83907494    31463271    7  HPFS/NTFS
/dev/sda6        83907558   146834099    31463271    7  HPFS/NTFS
/dev/sda7       146834163   209760704    31463271    7  HPFS/NTFS
/dev/sda8       308335608   312576704     2120548+  82  Linux swap / Solaris

Your primary partition /dev/sda3 seems to be inside your extended partition /dev/sda2. I haven't seen anything like that, I haven't even heard you could create primary partition inside extended. Probably you can't, this looks like messed up partition table.

What is exactly your problem, you want to install on /dev/sda3 and you can't see it in manual partitioning during installation?

Do you have existing linux on /dev/sda3?

---

### Post by audiomick on 2010-02-01
Hi Darko.

> **darkod said:**
> 
Your primary partition /dev/sda3 seems to be inside your extended partition /dev/sda2. I haven't seen anything like that, I haven't even heard you could create primary partition inside extended. Probably you can't, this looks like messed up partition table.

I saw a thread about a week ago from someone who had done something like that, but I have no idea how he managed it. I don't know how he fixed it either, he stopped answering.

---

### Post by jocaps on 2010-02-01
> **darkod said:**
> Not sure what your problem is, because you didn't say (except the title), but this is very strange:

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    20980889    10490413+   c  W95 FAT32 (LBA)
/dev/sda2 [COLOR=Blue]20980890   312576704[/COLOR]   145797907+   5  Extended
/dev/sda3       [COLOR=Red]209760705   308335544[/COLOR]    49287420   83  Linux
/dev/sda5        20980953    83907494    31463271    7  HPFS/NTFS
/dev/sda6        83907558   146834099    31463271    7  HPFS/NTFS
/dev/sda7       146834163   209760704    31463271    7  HPFS/NTFS
/dev/sda8       308335608   312576704     2120548+  82  Linux swap / Solaris

Your primary partition /dev/sda3 seems to be inside your extended partition /dev/sda2. I haven't seen anything like that, I haven't even heard you could create primary partition inside extended. Probably you can't, this looks like messed up partition table.

What is exactly your problem, you want to install on /dev/sda3 and you can't see it in manual partitioning during installation?

Do you have existing linux on /dev/sda3?

Ok sorry for not specifically writing in the subject of my post. Yes.. I want to install Ubuntu from the Ubuntu 9.04 CD and I couldnt because while installing Ubuntu cannot see the partition (but by just browsing the partition in a filemanager I can see them when outside the installer application).

Nope there is no existing linux. I created those partitions manually using Acronis Partition Manager (forgot the version). I made a 2 primary partitions (or I thought that was what I did). One was Fat32 10Gb for WinXP (sda1), then around 30Gb as extended logical NTFS's (sda5, 6,7). Another primary of around 44Gb Ext3 (sda3) and then a Swap of 2GB (sda8). 

I guess sda3 is shown as extended.. thats the problem. I do believe I made this also primary. I can reformat,move or do whatever with all the partitions except sda1 (since I already installed winxp there.. though not so heavy, its still an empty winxp.. but I wouldnt like removing it as I have ahci issues with winxp and it took me quite a lot of work till I made it working.. and it will happen again if I want to reinstall winxp).

You want me to delete sda3 and sda8 and see if Ubuntu can then figure out what my paritions are?

---

### Post by darkod on 2010-02-01
That might explain it. In future, I recommend to NOT use Acronis Partition Manager. I haven't used it, have nothing against it, but you always have Gparted in the ubuntu livecd and it looks like it's doing much better job.
Because this strange layout was created by Acronis, I would recommend:
Delete /dev/sda3 (the 44GB linux partition) and /dev/sda8 (the swap partition) with Acronis again, same progam that you created them with.
Reboot and make sure XP is happy. After that, you have two options:
If you still want to create partitions manually, do it during the ubuntu install process. Alternatively if you want them prepared in advance, create them using Gparted from the live desktop.
The other option is to leave that space (44GB + 2GB) as unallocated and it should be unallocated after deleting the partitions with Acronis, and during the ubuntu install process tell it to Use Largest Available Free space. That will create default / and swap partitions inside the unallocated space. No need for manual intervention.

---

### Post by jocaps on 2010-02-01
Thanks darkod. I'll keep GPart in mind next time I do this. I deleted the Linux partitions and got things worked (i.e. I let Ubuntu use the largest continuous free space and make its own swap and working partition without me manually doing it). So please mark this as SOLVED! :)

---

