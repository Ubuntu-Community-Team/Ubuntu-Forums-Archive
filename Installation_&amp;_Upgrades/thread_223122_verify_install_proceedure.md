---
title: "verify install proceedure"
date: 2006-07-25
forum: Installation &amp; Upgrades
---

### Post by japats on 2006-07-25
Hello 

I would like to verify that I understand installing properly. 

I have two hard drives each with four partitions. The first partition on the primary drive is windows XP with NTFS.  The First partition on the slave drive had Xandros installed on it and is ReiserFS.  All the other partitions are FAT32(extended). I want Ubuntu on the old Xandros partition.  

What I think I should do, is make a new partition small partition for swap and then when I select mount points in install use "/" for the old Xandros partition, and swap for the new small partition, and /windows for all the other partitions.  Can use /windows for them all or do I need to do /windows1, /windows2 ...

This will not affect any data on the windows partitions? 

Should I select the option to format the "/" and Swap partitions? 

Also in the live cd mode, I can't browse the hard drives, is this normal? 

Thank you.

---

### Post by Herman on 2006-07-26
> What I think I should do, is make a new partition small partition for swap and then when I select mount points in install use "/" for the old Xandros partition, and swap for the new small partition, and /windows for all the other partitions. That sounds alright to me, you just mount all your FAT32 as /Windows when you use the 'Alternate' CD, I presume the "Desktop CD is the same, but I'm not sure. > Should I select the option to format the "/" and Swap partitions?  Yes, you should, definitley. > This will not affect any data on the windows partitions?  No, normally it does not, but you should always make sure that you have your data backed up on some other media and also have your re-install CDs for all other software just in case.  > Also in the live cd mode, I can't browse the hard drives, is this normal?  Yes, that is normal. Before we can browse any other drives in most Linux systems whether installed or from a Live CD, we need to mount them first.
Mounting involves [LIST=1]
[*]finding relevant information about our partitions
[*]making a mount point .
[*]mounting the other filesystem at the mount point with the correct syntax[/LIST]1. To find exact information about our partitions, the easiest way these days. is to go 'System' -->'Administration'-->'Gnome Partition Editor', and there you can see exactly what you have. Make special note of the numbers for the partitions, for example, if Windows is called /dev/hda1, and Ubuntu is /dev/hdb1, and your FAT32 partitions are /dev/hdb5 and /dev/hdb6, maybe. *I'm just guessing here, you need to check these you yourself to make sure you get these right, okay?*
You can also do ```
sudo fdisk -lu
``` 
2. A mount point is just a folder that you can open to see the other filesystem you have mounted. We usually make that other folder with a command from our terminal, such as the following one if you want to make a folder (directory) named Windows inside your /media directory, which is one of the customary places to make such mount points, ```
sudo mkdir /media/windows
``` ```
sudo mkdir /media/data
``` You 'mount' the other filesystem with a command find your terminal too, for example, sudo mount /dev/hdxx /media/data
```
 sudo mount /dev/hdxx /media/windows -t ntfs -o nls=utf8,umask=0222
``` Note: replace '/dev/hdxx' with whatever you found out in Gnome partition editor is the real name for your Windows partition ```
sudo mount /dev/hdxx /media/data -t vfat -o umask=000
``` Note, replace /dev/hdxx with whatever you found out in Gnome Partition Editor is the actual name for one of your data partitions.

 After that you should be able to open your /home/ubuntu directory (folder) and go up two levels in your filesystem to the top of your filesystem, (called root or designated with the slash symbol as follows; /
Then you open your /media directory. Inside it will be your two mount points, one called 'data' and another called windows.
(You can make two called data if you want, just call one data_one and the other data_two or something, when you make them in terminal).
You can 'read' NTFS filesystems and copy the files, but not 'write', meaning paste anything into it or alter any files.
With FAT32 you can do anything, copy, paste, open files with Ubuntu apps and change them, anything you like.

Regards, Herman :D

---

### Post by japats on 2006-07-27
Thank you.

I will be trying the install in a few days.

---

### Post by japats on 2006-07-30
Hello When trying to install, after going to set up partitions Iget an error message " information sector has wrong signature (0)".  This refers to a fat32 partition.  Not one that ubuntu will install.  It says I can ingnore and go back a fix.  I have used teh windows check disk and defragment and still get the error.

Can just not mount this disk?

What will the conseqenses of that be?

Thanks

---

### Post by Herman on 2006-07-31
Hello, japats, Could you boot the Live CD and open a terminal and enter the following command and post the output of that here please?
```
sudo fdisk -lu
``` Can you still mount the partition with the problem and access all the files with the Live CD? Can you still access all the files from Windows?
>  Can just not mount this disk? Probably you can just not mount that partition during the install process. It shouldn't matter at all, it's just that you won't have the convenience of having the partition pre-mounted automatically every time Ubuntu boots up. You can mount it later. 
However, it still makes me worry if there might be something wrong and I'm wondering if it should be fixed first or if it's okay to fix it later.> All the other partitions are FAT32(extended) I take this to mean all your FAT32 data partitions are 'logical' ones, inside an 'extended' partition. Which means this issue has nothing to do with the four partition per disk limit. (Just checking to make sure I'm clear on that). Otherwise we might need to move some of your data and make some new arrangements. 
Didn't Xandros have a swap area already? It's Linux, so I assume it would have, but maybe not.
Does this problem partition come up with a black rectangle in GParted? 
Regards, Herman :D

---

### Post by japats on 2006-07-31
Hello Herman,

Thank you for the reply.

The results from fdisk -lu are dev/hdb5 start 50267448 end 70509284 blocks 10120918+ ID b W95 FAT32.

I was able to mount it from the live cd, and everything looked good.  However, it shoed as 9.65GiB with only 0.03MB free.  There is more space on the disk.  At one time it was nearly full, but I have since cleared off about 3GB of space.

On Gparted it shows up as blue inside a green box.

Another that I did, when splitting out space for the swap partiion on the primary part of the drive at first I accidently created a 2 MB partition instead of a 2 GB partition.  But that partition never showed up in gparted or the install proceedure.

Thanks again,
jp

---

### Post by Herman on 2006-08-01
Thanks, japats, 
I was really hoping you might show me the *entire* output from sudo fdisk -l or sudo fdisk -lu, rather than just one line. :D I'm still not clear on how many primary partitions and how many logical partitions you have on each disk and on what sectors or cylinders (disk order).
The output of that command will tell me or another person who knows how to read it quite a lot of useful information about the state of your hard disks and partitions. Without the whole thing I am really still 'in the dark' and unable to give you any real re-assurance.
But that's okay. :D
It is good that you partition still comes up in color in GParted and can be mounted okay in the Live CD and read alright. Probably that means everything is okay. > All the other partitions are FAT32(extended) If you mean 'logical' (inside and extended partition), then it's probably okay to  just complete you install as normal, but don't bother mounting the one with the problem for now. You can  manually mount it later. If you can mount it and read it with the Live CD it should be moutable from your new hard-disk installed system as well.
Good luck with it, any more questions, feel free to ask, Regards, Herman :D

---

### Post by japats on 2006-08-02
Hello,

Thank you for your quick reply again , Herman.

Here is the complete output of fdisk -lu

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63    29655989    14827963+   c  W95 FAT32 (LBA)
/dev/hda2        29655990   156296384    63320197+   f  W95 Ext'd (LBA)
/dev/hda5        29656053    69979139    20161543+   b  W95 FAT32
/dev/hda6        69979203   109675754    19848276    b  W95 FAT32
/dev/hda7       109675818   156296384    23310283+   b  W95 FAT32

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes



   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    44692829    22346383+  83  Linux
/dev/hdb2        50267385   312576704   131154660    f  W95 Ext'd (LBA)
/dev/hdb3        44692830    50267384     2787277+  82  Linux swap / Solaris
/dev/hdb5        50267448    70509284    10120918+   b  W95 FAT32
/dev/hdb6        70509348    91538369    10514511    b  W95 FAT32
/dev/hdb7        91538433   131347439    19904503+   b  W95 FAT32
/dev/hdb8       131347503   210612149    39632323+   b  W95 FAT32
/dev/hdb9       210612213   312576704    50982246    b  W95 FAT32

Partition table entries are not in disk order
ubuntu@ubuntu:~$

Disk /dev/hda1 is actually NTFS, which I thought that is what it showed up as when I first looked at it, but here it shows up as W95.

/dev/hdb5 is the partion that was giving me errors.  I reformated it and put the data back on, and I got the same error (although when I mount it from the live disk it now shows that is not nearly full, as it had before).  so changed the option in install to not mount it, but I still get the same error.  I ignored the error and tried to continue and got a second error, that said it showed 0 zero clusters instead of "some large number".  I continued to ignore and got the same error for another partition hdb7.  I aborted install.  I can browse the partitions on the live disk also.

What I am mainly worried about it losing the information on the disks. It would take a long time to get everyhting back and set up again.

Thanks again.

---

### Post by Herman on 2006-08-02
japats, Thank you for the fdisk output. I have analysed it and now I can see exaclty what is there.  I can't see anything wrong with your fdisk output here (except as you say, /dev/hda1 should be NTFS). Your swap area is 'Primary', which is okay. In Ubuntu the swap area is more often made as 'logical', but that doesn't matter, swap can be 'Primary' or 'Logical'.

I can see now that what you are trying to do is feasible and should not be any problem for a partitioner that is working properly on disks that have a healthy partition table.
I think you made the best decision in aborting your install. Something seems to be wrong, but it isn't anything obvious to me.
You might try installing with the 'Alternate' CD instead of the 'Desktop' CD and see if that will work. If it does, maybe there's a bug in the 'Desktop' CD's Installer/partitioner.
If the 'Alternate' Install CD doesn't recognise your partition table either, which may very well turn out to be the case, then maybe there is some incompatibility between the 'Parted based partitioners and the partitioning software that has written you partition table previously at some stage. I'm not sure if that can happen, but it seems that way to me. Otherwise I just don't know. It's odd that fdisk thinks /dev/hda1 is FAT32 but you say it's NTFS.

You are right to be cautious, you should back up all your data before doing any disk partitioning work. An external 2.5" USB drive in a caddy cost me about $120  Aust. for the 40.0 GB disk and $20 for the  caddy  (case).  It's enough to hold thousands of dollars worth of music files and keep them safe. Some files might be worth a lot more than that if they contain details of business transactions or something like that. It's really well worth investing in  some kind of back-up media that is spaceous, fast, easy to use, economical and safe. External USB drives are great.

I am not expert enough to be able to help you more than this, I hope the 'Alternate' Install CD will do it for you. Regards, Herman :)

---

### Post by jrjr on 2006-08-02
.

---

