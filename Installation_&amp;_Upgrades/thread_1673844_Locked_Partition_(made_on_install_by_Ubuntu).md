---
title: "Locked Partition (made on install by Ubuntu)"
date: 2011-01-23
forum: Installation &amp; Upgrades
---

### Post by mousethief on 2011-01-23
I had Ubuntu 10.04 on this machine and wanted to convert it to a dual boot. It's a 500GB hard drive. The HDD had 3 partitions: one really big one, and two swap areas of about 6 GB each.

I ran GParter and carved the big partition into a 100GB partition and a 400GB partition (less the swap areas). Then I installed Windows XP into the 100GB partition, then installed Ubuntu 10.04, selecting the "create dual boot" option. 

It dual boots beautifully, and everything runs just fine. But I find that Ubuntu has split the 400 GB partition into two 200 GB partitions, and one of them is simply off-limits. I can see it, but I can't write to it. 

The attached png shows the Disk Utility, with the mystery partition selected.

Its only contents is a folder called lost+found; I cannot open it.

---

### Post by coffeecat on 2011-01-23
I don't know why or how the installer split your 400GB like that, but what you seem to have ended up with is:

Windows - sda1
199GB primary partition formatted ext4 - I'm guessing that this is your "locked" partition since you've mounted it to a mountpoint in /media.
202GB extended partition containing a 190GB ext4 partition (probably your Ubuntu root partition) and two swap partitions.

The reason it appears to be locked is that it has been mounted by root and unless you invoke root privileges you cannot write to it - for the time being. That is easily dealt with and I can tell you how to "own" it if you wish. Ignore the lost+found folder. That's quite normal for a Linux filesystem; it's used to hold recovered files after a filesystem check in the event of filesystem corruption.

A question. What do you want to do with the 199GB partition? Instead of arranging for it to be mounted so that you can write to it as a normal user, you could reformat it NTFS so that it can be used by both Windows and Ubuntu.

To be sure I have interpreted your disk utility screenshot correctly, please open a terminal and post the output of these two commands:

```
sudo fdisk -lu
df -h
```By the way, a 190GB Ubuntu root partition is enormous. Many people prefer to have one of about 15-20GB and then have a separate home partition or a separate data partition. A separate data partition is conveniently formatted NTFS if you are also using Windows - as I mention above. 

Also, why two swap partitions? That's very unusual.

---

### Post by mousethief on 2011-01-23
Hey, coffeecat, thanks for responding! Love your avatar.

Okay here's the result of the fdisk command:

PRINTOUT STARTS
------------------------------------------------------------------------------------------------------

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000752dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   192946319    96473128+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2       192956715   582487288   194765287   83  Linux
/dev/sda3       582488062   976773119   197142529    5  Extended
Partition 3 does not end on cylinder boundary.
/dev/sda5       964745216   976773119     6013952   82  Linux swap / Solaris
/dev/sda6       582488064   952715263   185113600   83  Linux
/dev/sda7       952717312   964734975     6008832   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 203.9 GB, 203928108544 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0ed9d69f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   398283479   199141708+   7  HPFS/NTFS
----------------------------------------------------------------------------------------------
PRINTOUT ENDS

And here is the result of the df command:

PRINTOUT STARTS
----------------------------------------------------------------------------------------------
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda6             174G   64G  102G  39% /
none                  999M  332K  999M   1% /dev
none                 1003M  200K 1003M   1% /dev/shm
none                 1003M   84K 1003M   1% /var/run
none                 1003M     0 1003M   0% /var/lock
none                 1003M     0 1003M   0% /lib/init/rw
/dev/sdb1             190G  145G   46G  77% /media/Ubermaus
------------------------------------------------------------------------------------------------
PRINTOUT ENDS

As to what I want to do with it: I want to store music and photographs, mainly. I don't have enough to swamp the 200GB boot partition yet, but I've only ripped maybe 1% of my CDs.

The swap partitions were on the machine when I got it - it's a refurb from eBay and the seller preloaded Ubuntu 10.04. 

I'm something of a Linux noob and am trying to learn as much as I can so I don't have to ask so many stupid questions! If I do NFTS this thing so I can reference it from both Windows and Ubuntu, how do I refer to it in Ubuntu? I'm of course used to the Windows method of referring to files with the drive letter and then the directory structure; What is the equivalent in Linux? I'm guessing it starts with file://

(I've ordered the Mark Sobell book; I'm sure it will answer most of my idiot questions!)

---

### Post by mousethief on 2011-01-23
Oh, and re. the huge boot partition: I just let the Ubuntu installer do whatever it wanted; I gave it 400GB to play with, and this is what I got.

---

### Post by coffeecat on 2011-01-23
OK, the terminal outputs confirm what I thought. Your spare partition is a primary, sda2, and your Ubuntu partitions are logicals in the extended, sda3.

If you're wanting to store music and photos the easiest thing would be to convert sda2 to NTFS. It will appear in Windows as D: or E: or whatever drive designation it gives it. And in Ubuntu you can simply mount it as needed from the Places menu.

Open Disk Utility, highlight the spare 199GB sda2 partition and reformat it as NTFS. While you have Disk Utility open give it a partition label, something like "Data" - whatever you want. You should now be able to see it in the Places menu and if you click on it a Nautilus file browser will open and you will be able to read and write to it. If it doesn't appear immediately simply do a reboot. And when you're next in Windows it should appear in My Computer.

As you can see the partition will only be a mouse-click away, but if you want it mounted on bootup with a desktop icon, post the contents of your system file /etc/fstab. Go to Places and click on Computer. Now open 'Filesystem' and open the /etc folder. Double-click on the fstab file and it will open read only in a text editor. Copy and paste that into your post. Please use code tags to enclose the fstab text to make it readable. You can use the # icon in the message toolbar for this. Please also post the output of:

```
sudo blkid
```... also in code tags.

> **mousethief said:**
> Oh, and re. the huge boot partition: I just let the Ubuntu installer do whatever it wanted; I gave it 400GB to play with, and this is what I got.

For your information - the partition sda6 should be referred to as your root (designated '/') partition, not boot. A boot partition is something else and contains files associated with the kernel and with the grub bootloader. You don't have a separate boot partition - all your boot stuff is in /. Just so you don't get confused by the terminology when you come across people talking about a boot partition.

---

### Post by mousethief on 2011-01-23
Before doing anything:

/etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=49592cc3-ee0c-41fe-ae4d-ebd6cf777676 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=ac71cc74-5477-4695-92b6-ae94d21d8d84 none            swap    sw              0       0
```output from blkid:
```
/dev/sda1: LABEL="Windows Partition" UUID="FC38FBF738FBAF30" TYPE="ntfs" 
/dev/sda2: UUID="82f897c0-7057-4577-bbfa-24bd5ac7262d" TYPE="ext4" 
/dev/sda5: UUID="4512fa5b-d7b1-4c3c-a6d1-51fbf790020d" TYPE="swap" 
/dev/sda6: UUID="49592cc3-ee0c-41fe-ae4d-ebd6cf777676" TYPE="ext4" 
/dev/sda7: UUID="ac71cc74-5477-4695-92b6-ae94d21d8d84" TYPE="swap" 
/dev/sdb1: LABEL="Ubermaus" UUID="F8F0E79DF0E75FFC" TYPE="ntfs" 
```

ETA: And thanks for the heads-up on the nomenclature.

---

### Post by coffeecat on 2011-01-23
I'll be logging off in a moment so I won't be able to post again until tomorrow. If you want the sda2 partition included in your /etc/fstab so that it is mounted on bootup you'll have to repost the output of 'sudo blkid' after you reformat sda2 to NTFS. The command blkid gives us the UUIDs of the partitions. The UUID  changes after a partition is re-formatted so the current UUID of sda2 will be of no use once that partition is reformatted.

I forgot to mention your sdb1 partition (the only partition on your 204GB drive). That's already formatted NTFS so that could be included in fstab if you want. It should already be appearing in Places as 'Ubermaus'.

---

### Post by mousethief on 2011-01-24
Okay I was able to get into the locked partition by simply giving myself rights to it with chown. 

Now I want to scrap the dual-boot and just boot to Ubuntu. I will run whatever windows Apps I need through VirtualBox. Since you have a good idea of what I have, can you tell me how to undo the dual boot without destroying everything that's already in my root partition? I looked at some other threads but their setups were different as far as extended partitions and such, and I was afraid to do something that applied to their systems, and find it didn't work with mine. 

I would also like to recombine the windows partition and the formerly locked partition if that's possible. 

Thanks again for your help.

MT

---

### Post by coffeecat on 2011-01-24
What I would do is, firstly, install Gparted. If you're going to do some serious partitioning work, it's better. Don't get me wrong, Disk Utility is excellent, but you'll find Gparted easier and more powerful for this sort of thing. Once installed, you'll find it in System > Administration.

If you're sure you want to remove Windows, simply open Gparted and delete the Windows partition, sda1. Remember that with Gparted, you have to 'Apply' any pending operations - with the big green tick button. Now you can do one of two things. Either enlarge the sda2 partition backwards into the space freed up from sda1, but this will take hours I warn you. You may find that once sda1 has been deleted that sda2 has been renumbered to sda1 - or possibly not. Also you should backup any data you have on sda2 before resizing. Any resizing/moving of partitions has the potential to go horribly wrong.

But since you need to backup evrything on sda2, the second option is to delete sda2 as well as sda1, and then make one big primary partition in the freed space. This will be much quicker than resizing the original sda2.

Once you've done all that you'll find that Windows is still in the grub boot menu. Simply open a terminal in Ubuntu, and:

```
sudo update-grub
```Here's a useful link for you:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Although you already have a setup, you may find it useful to read through that, together with all its links. It tells you most of what you need to know about partitions when using Ubuntu.

Good luck!

---

### Post by mousethief on 2011-01-24
Thanks! I'm going to sit on this and ponder for a while, I think, before making any big decisions. Thanks for all your help!

---

