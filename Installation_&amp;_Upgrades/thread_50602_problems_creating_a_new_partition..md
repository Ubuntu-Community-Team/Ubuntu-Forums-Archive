---
title: "problems creating a new partition."
date: 2005-07-20
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2005-07-20
I am very happy with Ubuntu after installing about amonth ago.  I hardly ever use XP any more.  So I thought I would trim 10gb off the ntfs partition and turn it into a fat32 partition for file sharing.
The trimming of ntfs went well.  (I had defragged it beforehand.) I used the ubuntu install disc partitioner.
However, when I try to create a new partition in the unallocated 10gb, the new partition option is always greyed out.
This is the same whether I am using the install disc partitioner, gparted, qtparted or xp file manager.

Any help would be greatly appreciated. :) 
I realise you probably need to see a list of the  partitions, but I don't know how to do that. :-?

---

### Post by Xian on 2005-07-20
My best guess would be that you already have four primary partitions and without creating an extended partition you will be unable to make any further additions. Listed below is a command to see your partition scheme:
```
$ sudo fdisk -l
```

---

### Post by aum11 on 2005-07-20
Thanks Xian.  Here is the output,and it seems you are right about the 4 primary partitions.
How can i rearrange things, please?

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196   de  Dell Utility
/dev/sda2   *           8        3655    29302560    7  HPFS/NTFS
/dev/sda3            4872       11861    56147175   83  Linux
/dev/sda4           11862       12161     2409750    5  Extended
/dev/sda5           11862       12161     2409718+  82  Linux swap / Solaris

---

### Post by Xian on 2005-07-20
No, you have an extended partition right there on /dev/sda4 so that is not the cause of your problem. If you used the InstallCD for your initial partitioning then that in and of itself would explain why you can't create a new file system out of your free space with gparted or qtparted, since the InstallCD for some reason only makes the extended blocks as large as the last partition requires. It's very odd and I've never really understood it, but that is what it does. 

However, that should not prevent you from using the InstallCD again to make further revisions. There is some other conflict here which at present I do not see.

The fdisk command will not illustrate your free space under the InstallCD partitioning, but the command listed below will. Look and see how much room it outputs for your HD. Tab to 'quit' when finished to exit the command.

```
$ sudo cfdisk
```

---

### Post by aum11 on 2005-07-20
Here is the output Xian.                              cfdisk 2.12p

                              Disk Drive: /dev/sda
                       Size: 100030242816 bytes, 100.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 12161

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   Dell Utility                        57.58
    sda2        Boot        Primary   NTFS             []              30005.83
                                      Unusable                         10001.95
    sda3                    Primary   Linux ext3       [/]             57494.71
    sda5                    Logical   Linux swap / Solaris              2467.59

---

### Post by Xian on 2005-07-21
I'm not seeing the free space in that output.
Here's mine:
 
```
 
hda1                    Primary   NTFS                         26853.09
hda2        Boot     Primary   Linux ext3                 12880.79
hda3                    Primary   Linux ext3                  24997.11
hda5        NC        Logical   Linux swap / Solaris    1006.36
hda6                    Logical   Linux ext3                     5000.98*    
hda7                    Logical   Linux ext3                     29998.08
hda8                    Logical   Linux ext3                     12099.39
Logical   Free Space                       47196.66
```

---

### Post by aum11 on 2005-07-21
Xian,
it is the space shown as unusable.
 Unusable 10001.95
All I did was to use the Ubuntu install disc to remove the last 10gb of the ntfs partition.
Why is it shown as unusable rather than logical free space?
What to do?
Thanks.

---

### Post by Xian on 2005-07-21
It _might_ be possible that you need to go in with the InstallCD partitioner and remove sda5 so that you can then reset the size of sda4, thus allowing you to use that free space. Immediately place the swap file back on sda5 and then see if you can create a fat partition on sda6. Don't write anything to disk until you see if this is accepted.

---

### Post by aum11 on 2005-07-21
Major dramas last night!!!

Using the Ubuntu install cd, I deleted the swap partition successfully.

Then  I went into xp and disk manager and was now able to create an extended fat32 partition.

Then went back to the Ubuntu install cd to try to recreate the swap file.  No luck. 
 Once again the space was classified as unusable.

Worse still was that when I attempted to reboot  a grub error 17 came up every time.  
Eventually by persevering I was able to recreate grub.

So right now, I have no swap partition.
It seems that I need to change one of my partitions from primary to extended.  Is this correct?  If so, how is this done?

Thanks for all the help.  I am getting there!!!!!!!! :)

---

### Post by Xian on 2005-07-21
The only change you should have made from your post was to create the extended partition first, and then make your fat file system and swap file. By making the fat partition before the extended one, you have created a scheme with four primary partitions, and this will not allow room for the needed extended space.

Notice the sequence I previously mentioned:

1. Reset the size of sda4 (extended partition)
2. Place the swap file back on sda5
3. Create a fat partition on sda6

This can all be fixed by just redoing the partitioning.

---

### Post by aum11 on 2005-07-21
Thanks Xian for your help.

Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           7       56196    6  FAT16
/dev/sda2   *           8        3655    29302560    7  HPFS/NTFS
/dev/sda3            3656        4871     9767520    f  W95 Ext'd (LBA)
/dev/sda4            4872       11861    56147175   83  Linux
/dev/sda5            3656        4871     9767488+   b  W95 FAT32

As You can see, sda5(fat32) was made  extended.

I am confused.

Gparted says that I already have  4 primary partitions. :-? 



                                 cfdisk 2.12p

                              Disk Drive: /dev/sda
                       Size: 100030242816 bytes, 100.0 GB
             Heads: 255   Sectors per Track: 63   Cylinders: 12161

    Name        Flags      Part Type  FS Type          [Label]        Size (MB)
 ------------------------------------------------------------------------------
    sda1                    Primary   FAT16          [DellUtility]        57.58
    sda2        Boot        Primary   NTFS             []              30005.83
    sda5                    Logical   W95 FAT32                        10001.95
    sda4                    Primary   Linux ext3       [/]             57494.71
                                      Unusable                          2467.59


In my ignorance, I cannot see 4 primary partitions.

Can you please suggest steps using these new partition numbers.
Thanks so much.

---

### Post by Xian on 2005-07-21
Yeah, what you've done there is to create an extended partition on sda3 but it only holds the FAT32 file system, while sda4 sits on a primary partition and that prevents the extended space from being enlarged for such things as additional FS's or swap files. 

Here is ideally what your scheme should look like:

sda1 FAT16
sda2 NTFS
sda3 Linux (Ubuntu)
sda4 Extended
sda5 Swap
sda6 FAT32

If you are using the InstallCD you don't have to tell it to make an extended partition. Just go ahead and do the first three, then when you tell it you want to create sda5 it will automatically start the extended space. Basically, it will just appear without you ever having to create it manually. Likewise, when you make sda6 it will also be placed in the extended range, and this will continue up to the point your HD becomes fully used. The extended space won't even show up in the InstallCD partitioner user screen, but it is definitely there since no drive can have more that four partitions without an extended resource.

The nice thing about using the InstallCd is that it will automagically manage your extended partition range so you can worry about just the file systems. But the downside is that it not compatible with qt/g-parted. This is not a problem unless you only care to use the parted GUI's. I use the InstallCD and have found it to be completely reliable.

As to how to reach this point without corrupting your current sda4 is another matter. I don't know if it is possible, so I'd either back everything up on that partition that you need, or just do another default install session after setting the new scheme.

---

### Post by aum11 on 2005-07-21
Thanks Xian.  I really appreciate the effort You have put into this.  Ta.
I am obviously not keen to mess around with the Linux partition which I have spent many days crafting to satisfaction.
I am still looking for some easier alternativesl.
There are some basic questions I need answered to help me come to a decision.
Why does it think there are 4 primary partitions?
Why can't I simply change the linux partition from primary to extended? and then have only 3 primary partitions?

---

### Post by Xian on 2005-07-21
[QUOTE=aum11]
Why does it think there are 4 primary partitions?[/quote]
Probably due to gparted not being compatible with the method that the InstallCD uses to create extended partitions. I mentioned the oddity of this earlier and have no explanation for why this type of procedure is used. Not that it is bad or wrong, but it is somewhat uncommon. 

Or it could be something else that I'm not familiar with.

[QUOTE=aum11]
2.Why can't I simply change the linux partition from primary to extended? and then have only 3 primary partitions?[/QUOTE]
Because a file system can not reside _as_ an extended partition. It can be placed within it, but this can only be done after the extended area is created, and there must be room in the extended space for the desired partition. Your extended partition is already fully occupied with sda5. If you remove it everything that resides within those blocks will also be displaced. 

The problem actually isn't that you don't have four primary partitions and gparted says that you do. The real issue is that your extended partition is full and cannot be expanded without removing sda4 and sda5. Until this is fixed you have to live with what you have currently setup.

---

### Post by aum11 on 2005-07-21
Thanks Xian,
that clears things up for me.
Is there a safe and straightforward way for me to save the whole linux partition?
If so, is it then a case of deleting the linux partition, expanding the extended partition,creating an extended partition for linux and restoring the backup?
Then I can create an extended swap partition after that.
Have I got it clear?
Obviously the backup and restore procedure is key.
Sorry to be so pedantic, but this is big time as I am sure You are aware.  So much time has gone into this setup!!

---

### Post by Xian on 2005-07-21
[QUOTE=aum11]Is there a safe and straightforward way for me to save the whole linux partition?[/quote]
[Backup and Restore Your System](http://www.ubuntuforums.org/showthread.php?t=35087)

[QUOTE=aum11]If so, is it then a case of deleting the linux partition, expanding the extended partition,creating an extended partition for linux and restoring the backup?
Then I can create an extended swap partition after that.
Have I got it clear?[/quote]
You don't create multiple extended partitions. On most drives people will start out with three primary partitions, then make an extended partition for the remainder of the HD. This single extended partition is then segmented into further partitions. If the extended partition gets removed all the others that are within that particular space go with it. That is one of the differences between it and a primary partition. When a primary partition gets altered it usually only affects that specific disk area.

If you are using the InstallCD all you want to do is remove everything except for sda1 and sda2. Then start with the partition scheme that I posted earlier. 

sda3 Linux (Ubuntu)
sda4 Extended
sda5 Swap
sda6 FAT32

Again, don't worry about the extended partition as it will be created automagically. The only thing you need to do is instruct the installer of the sizes, filesystems, and mount points for sda3, sda5, and sda6. It will set up and manage the extended partition for you.

---

