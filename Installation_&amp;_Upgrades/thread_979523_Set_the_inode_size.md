---
title: "Set the inode size?"
date: 2008-11-12
forum: Installation &amp; Upgrades
---

### Post by angelkiller on 2008-11-12
Hello,

I was following [this guide](http://ubuntuforums.org/showthread.php?t=568731) which is on how to create an effective dual-boot setup with XP and Ubuntu. One of the steps requires that I install a program in Windows that will allow me to read/write ext2/ext3 file systems. However, the ext3 partition could not be accessed. After some research I found out that the software only supports ext2/ext3 file systems that have an inode value of 128. My fresh install of 8.10 had an inode value of 256.

Now, my question is how do I change the inode size. I've read that I can't just 'change' it, I have to reformat the partition. Since it's a new install, that's not a problem. But during the installation I don't recall any options where I could change the inode value. So how do I re-format my ext3 partitions to have an inode value of 128? Do I use the live CD or some other method?

Thanks. :)

---

### Post by cariboo on 2008-11-12
Have a look at this:

```
man mke2fs
```

or use a different program to acces youext3 partition from Windows

[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

[http://www.fs-driver.org/](http://www.fs-driver.org/)

[http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)

are some other prgrams that are available.

I think you are a  bit confused, Linux by default formats with a default block size of 1024, which means no matter how small the file is it takes  up 1k of hard drive space. All three of the programs work with the default block size. I've tried all three programs and they work.


Jim

---

### Post by angelkiller on 2008-11-12
I was using the program from fs-driver.org. I installed it and set the ext3 partitions as D: and E:. However, I could not accesss them. Windows says the disk is not formatted. The [troubleshooting page](http://www.fs-driver.org/troubleshoot.html) says that the drive was not mounted and to run a diagnostic utility. The utility gave me this:
[quote="Diagnostic Utility"]C:\mountdiag D:
The volume has an Ext2/Ext3 file system, but the Ext2 IFS 1.11 software did not mount it because the file system has an inode size unequal to 128 bytes (inode size: 256 bytes). The only way to solve it is to back up the volume's files and format the file system: give the mkfs.ext3 utility the -I 128 switch. Finally, restore all backed-up files. After that, the Ext2 IFS software should be able to access the volume.[/quote]
After re-reading the error, I may have misunderstood what it says. Anyways, I just want to be able to have full access to my ext3 partitions from Windows, just like any other ntfs partition. Does the command above still apply to me?

Thanks again.

---

### Post by iponeverything on 2008-11-12
I love errors that are useful. The one that you posted is clear as a bell. If you want use that program to access your linux partition it's going to need formated with an inode size of 128k -- 

cariboo907 -- I think you misread his post, he not talking about block size.

Yes, the the error is valid for you.

use:
sudo tune2fs -l /dev/sda2 | grep Inode

to see your inode size. Its seems to me that having to reformat is bit
drastic, you should another program to access your linux partition that is not so picky.

---

### Post by Steve1961 on 2008-11-12
Since Intrepid the default inode size for ext3 partitions formatted with the Intrepid installer is 256, all previous versions set it at 128.  This has caused a few issues, especially with windows based cloning software such as Acronois True Image. If you upgraded an existing installation the inode size will still be 128, but I don't think you can convert from 256 to 128.  One option would be the use somethimg like a live gparted or Ubuntu Hardy cd and create and format the partitions with that.  Then install Intrepid but ask it not to format the partition.

---

### Post by angelkiller on 2008-11-12
For the sake of completeness, I'd rather follow the guide exactly before I consider alternative methods. I want to have everything working as intended before I start changing things.

Right now, I'm going to try to use a live Gparted CD and reformat the ext3 partitions. I assume using the default settings in Gparted will give me an inode value of 128. We'll see.

Thanks for all the (really fast) replies! :)

---

### Post by angelkiller on 2008-11-12
[quote="Steve1961"]One option would be the use somethimg like a live gparted or Ubuntu Hardy cd and create and format the partitions with that. Then install Intrepid but ask it not to format the partition.[/quote]
Ok, I tried that and it worked. I can now access the ext3 partitions in Windows.

Thanks again for everyone's help. :KS

---

### Post by Steve1961 on 2008-11-12
> **angelkiller said:**
> Ok, I tried that and it worked. I can now access the ext3 partitions in Windows.

Thanks again for everyone's help. :KS

Glad it worked :)

---

### Post by kiff on 2008-11-13
I also have the same problem, but I would rather not have to re-install Ubuntu if I can help it.

When I installed Ubuntu I created a root partition, a boot partition and a home partition. I only want to access my home partition from Windows, so I was hoping it would be possible to copy the data on this partition to a removable drive, use the liveCD to reformat the partition, and then copy the data back onto the partition. Can anyone confirm whether this is likely to work, or if there is something I have missed?

---

### Post by angelkiller on 2008-11-13
I can't say for sure, but the error message I got in my [second post](http://ubuntuforums.org/showpost.php?p=6158725&postcount=3) seems to imply that you can move the data, format and put the data back. I would think it would work.

---

### Post by kiff on 2008-11-13
I'll give it a try, and let you know how it goes. If it doesn't work I can always re-install. Thanks for your help.

---

### Post by Orographic on 2008-11-15
> **Steve1961 said:**
> ... One option would be the use somethimg like a live gparted or Ubuntu Hardy cd and create and format the partitions with that.  Then install Intrepid but ask it not to format the partition.

I'm new to Ubuntu but am trying to get my head around this. How do I ask Gparted via the Hardy live CD not to format? 

I tried to install Intrepid yesterday over my Hardy install by removing Hardy and recreating the partition it was on but then got something like 'No root file system is detected.'

A simple rundown on how to use Gparted to setup Intrepid with 128 inodes or whatever they are called would be really great for beginners.

---

### Post by Steve1961 on 2008-11-15
> **Orographic said:**
> I'm new to Ubuntu but am trying to get my head around this. How do I ask Gparted via the Hardy live CD not to format? 

I tried to install Intrepid yesterday over my Hardy install by removing Hardy and recreating the partition it was on but then got something like 'No root file system is detected.'

A simple rundown on how to use Gparted to setup Intrepid with 128 inodes or whatever they are called would be really great for beginners.


if you boot with a hardy cd or a gparted cd just create the partitions you need manually.  For example, with hardy you should find the partition editor in the system/administration editor (which is just gparted).  Select the disk to partition from the drop down menu and create two new partitions.  One should be an ext3 partition and another should be a swap partition.  The ext3 partition can be any size you want, and the swap partition should be around one and a half to two times your ram up to a max of about 2GB.  You can create more complex partitioning schemes if you want but this is just for a simple setup.

Once done boot with the Intrepid cd and when you get to the partitioning stage select manual.  Then select the ext3 partition and hit edit.  Mount it as / but select the option not to partition it.  Then select the swap partition and again select edit and make sure it's set as swap (you don't need to mount this).

---

### Post by Orographic on 2008-11-15
Thankyou! That last paragraph was what I needed. Will look into it when I get some time. :-)

This is why I am sticking with Ubuntu, there is so much support here. I have also been reading various help files here on terminal and other things to get a handle on it all.

---

### Post by Orographic on 2008-11-15
> **Steve1961 said:**
> if you boot with a hardy cd or a gparted cd just create the partitions you need manually.  For example, with hardy you should find the partition editor in the system/administration editor (which is just gparted).  Select the disk to partition from the drop down menu and create two new partitions.  One should be an ext3 partition and another should be a swap partition.  The ext3 partition can be any size you want, and the swap partition should be around one and a half to two times your ram up to a max of about 2GB.  You can create more complex partitioning schemes if you want but this is just for a simple setup.

Once done boot with the Intrepid cd and when you get to the partitioning stage select manual.  Then select the ext3 partition and hit edit.  Mount it as / but select the option not to partition it.  Then select the swap partition and again select edit and make sure it's set as swap (you don't need to mount this).

Just on this issue. In your last sentence there: Do I also have to select 'not to partition' the swap file? Should this swap file be an extended partition?

---

### Post by Orographic on 2008-11-15
I followed Steve1961's advice and it seems to have worked great! Inserted the Hardy live CD and used Gparted to create ext3 and swap partitions. Then I inserted the live Intrepid CD and once it got to the Partition Manager, I selected manual and then just set up ext3 as root and didn't check the format box. 

I can now back up to and restored from Acronis no probs at all. The restore took about 3 minutes. :popcorn:

I know there are other ways to do this but for folk already using Windows its great to be able to still use the Acronis boot CD for imaging. I hope others find this thread useful. I'm a beginner Linux and Gparted user and I could do it no problems.

---

### Post by Steve1961 on 2008-11-16
> **Orographic said:**
> Just on this issue. In your last sentence there: Do I also have to select 'not to partition' the swap file? Should this swap file be an extended partition?


it can be a primary or extended partition.  Also, the partitioning of the swap partition probably doesn't matter, but better to be safe than sorry :)

---

### Post by mikex on 2008-11-16
> **Orographic said:**
> 

I can now back up to and restored from Acronis no probs at all. The restore took about 3 minutes. 

I ran into the same problems, but even though Acronis reports errors on the drive, it definitely does make a good image and does restore it properly, although, yes, it takes longer. I verified it works OK last night by restoring an image. Complete success. I'll just make images when I don't need the PC for a while.

---

### Post by kiff on 2008-11-17
> **kiff said:**
> I'll give it a try, and let you know how it goes. If it doesn't work I can always re-install. Thanks for your help.
In the end I didn't change the inode size, I found a different application for mounting ext3 partitions in windows: [ext2fsd]("http://www.ext2fsd.com/").

In some senses it's a little clunkier than Ext2 IFS, but it works, and it will do until the Ext2 IFS developers enable their app to use 256-bit inodes.

---

### Post by eks on 2009-03-10
Ok, I've [bumped ]("http://ubuntuforums.org/showthread.php?t=1090472")into exactly the same problem. I can reformat my /home to 128 bytes inodes, but I'd rather first understand it. What's the difference of having inodes of 128 or 256 bytes?

After reading [this]("http://magazine.redhat.com/2007/04/23/how-can-i-change-the-default-size-of-an-inode-when-i-create-an-ext2ext3-filesystem/"), I take is just extended attributes to the **Access Control List (what is that?)**. **And why Intrepid's default changed to 256 then?**

---

### Post by Cyan_Fire on 2009-03-10
As far as I know, increasing the inode size is a bit of future-proofing to allow for extra data fields for files (such as nanosecond timestamps, etc.). It does seem a little silly to me, but who am I to stand in the way of the future...

For all the folks that are reformating their partitions, you might want to make sure your drive UUIDs haven't changed or you might get weird symptoms when trying to hibernate, for example. (See /etc/initramfs-tools/conf.d/resume)

---

### Post by ollebolle on 2009-03-20
I ran into the same broblem!

I use grub for dualboot with Ubuntu 8.10 and Windows XP.
On windows I want to access the ext3 linux file system.
My inode is 256 since I used the partition manager on the latest installation CD.


**This program can handle inode 256!!** :)
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

It works fine! :P


These didn't work:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by wersdaluv on 2009-04-20
> **ollebolle said:**
> I ran into the same broblem!

I use grub for dualboot with Ubuntu 8.10 and Windows XP.
On windows I want to access the ext3 linux file system.
My inode is 256 since I used the partition manager on the latest installation CD.


**This program can handle inode 256!!** :)
[http://sourceforge.net/projects/ext2fsd](http://sourceforge.net/projects/ext2fsd)

It works fine! :P


These didn't work:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)
Does it read and write? It just reads for me.

---

### Post by leftos on 2009-05-01
Ext2FSD is quite buggy really. I know Ext2IFS is picky about the inode size but it's much more stable.

Ext2FSD corrupted the Linux partition on my friend's laptop on which Vista was pre-installed, and causes BSODs on my netbook when doing NTFS to EXT3 transfers over the network.

I myself wanted to give Ext2FSD a chance before reformatting, but now I'm only left with the latter option.

---

### Post by kiff on 2009-05-05
> **leftos said:**
> Ext2FSD is quite buggy really. I know Ext2IFS is picky about the inode size but it's much more stable.

Ext2FSD corrupted the Linux partition on my friend's laptop on which Vista was pre-installed, and causes BSODs on my netbook when doing NTFS to EXT3 transfers over the network.

I myself wanted to give Ext2FSD a chance before reformatting, but now I'm only left with the latter option.
That's really interesting, because I have been using it for a while now, and it works fine for me.

---

### Post by user2037 on 2009-06-09
I used Ext2-IFS on a Dm-crypted partition with 8.10. It appeared to work well enough, but upgrading to 9.04 made Ubuntu inaccessible. There were also issues with some garbage Windows files appearing in the Windows home folder; although, that may have been due to some combination of Truecrypt and the lack of any swap space (and memory ran out from time to time [causing crashes]).

---

### Post by Mike090830 on 2009-08-30
I had problems with the inode size of 256 bytes instead of the usual 128 bytes in ubuntu 9.04. My ext2 ifs and Acronis tools didn't recognize this partition anymore. :-(

Since I didn't want to reinstall the system, I backed up the system with tar, reformatted the partition with mke2fs and restored the files. Here's how it can be done:

Boot another linux, e.g. from another partition (I have 5 linux partitions 8)) or from a live CD.

1) Become root:
```
$ sudo -i
```

2) Check the inode size of the partition (I assume /dev/sda9 here) and note the UUID:
```
# dumpe2fs -h /dev/sda9
```

3) Mount the partition (if not done already):
```
# mount -v /dev/sda9 /media/sda9
```

4) Save all files of the partition in a tar archive on another partition, e.g.:
```
# tar -c -z -f /home/ubuntu904.tgz -C /media/sda9 ./
```

5) Unmount the partition:
```
# umount -v /dev/sda9
```

6) Reformat the partition (check /etc/mke2fs.conf and man mke2fs):
```
# mke2fs -v -I 128 -j -L ubuntu904 -U <original UUID> /dev/sda9
```

7) Mount the partition again:
```
# mount -v /dev/sda9 /media/sda9
```

8] Restore the data:
```
# tar -x -z -f /home/ubuntu904.tgz -C /media/sda9
```

9) Unmount the partition:
```
# umount -v /dev/sda9
```

10) If you had installed a grub boot loader in the partition, restore it:
```
# grub
grub> setup (hd0,8) (hd0,8)
grub> quit

```

\\:D/

Regards
Mike


[SIZE="1"]Keywords:
ubuntu 8.10, ubuntu 9.04, file system, unreadable, ext2, ext3, ext2 ifs, Acronis, partition, image, inode size, 128 bytes, 256 bytes, change, reformat[/SIZE]

---

### Post by ceefour on 2009-10-31
If you want to dual boot Ubuntu with Windows 7 and read ext3 filesystem, you can use Ext2FSD.

I’ve successfully used Ext2fsd on Windows 7 to read my ext4 (!) filesystem.

For those interested, the how-to is here: [Read ext3/ext4 Partition from Windows 7]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/")

Hope this helps!

---

### Post by sEssGambino on 2010-01-27
Hi All, i have the same problem. I was trying to access my ext3 (256) partition on Ubuntu from my Windows 7 (Dual-Boot). I tested all programs mentioned here and only have success on  Virtual Volumes from [http://www.chrysocome.net/explore2fs](http://www.chrysocome.net/explore2fs)
all the other software ask me to format the partition or simple doesn't show partition content. On Virtual Volumes´s Page they say that Vista version is still on development, but at this point only thing i cant do is to copy files to ext3 partition but my needs was to copy files from ext3 so this works perfect for me. Thanks for the help

---

### Post by ultranalog on 2010-04-27
Just another quick vote for ext2ifs and inode size of 128 bits.

I tried ext2fsd but it completely hosed my windows xp and repeatedly bluescreened my work laptop that I wanted to rsync to.

Explore2fs was not an option as I couldn't access it from Cygwin (my last hope for sanity under windows) and I wanted to script an rsync job.

So after a reformat to 128 bit inodes ext2ifs is working perfectly and I can finally rsync from home to my backup drive that I keep at work.

Thanks!

---

