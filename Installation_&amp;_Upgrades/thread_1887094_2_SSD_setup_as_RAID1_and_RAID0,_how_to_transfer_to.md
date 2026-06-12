---
title: "2 SSD setup as RAID1 and RAID0, how to transfer to?"
date: 2011-11-26
forum: Installation &amp; Upgrades
---

### Post by olddave1 on 2011-11-26
Hi,

Can anyone point me to a resource that explains the next step in getting my current 10.04 x86_64 installation (or a new install, whichever is easiest) across to my shiny new SSDs. The SSDs where setup according to this article - [http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux). Basically RAID1 for /boot and RAID0 for /

My current install is on a 200GB HDD, I'd prefer to install a new install on SSDs and take the opportunity to tidy up a bit, and copy across only some of my current /home directory.

Here is my fstab:

```

# UUID=4a6f85f4-1e1e-4552-b6d9-d45dae3a6942  /boot               ext3         noatime,nodev,nosuid,noexec         0  2
# UUID=2790a837-67d8-4ed5-b8d3-e1d36b0eb1f2  /                   ext4         noatime,nodiratime,discard,errors=remount-ro  0  1
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc               proc         defaults               0  0  
# / was on /dev/sda1 during installation
UUID=1e4e276c-8741-42e7-b52e-05c195790d28  /                   ext3         errors=remount-ro      0  1  
# swap was on /dev/sda5 during installation
UUID=251fcab2-d056-4f50-b91d-7a5f03652c71  none                swap         sw                     0  0  
/dev/scd0                                  /media/cdrom0       udf,iso9660  user,noauto,exec,utf8  0  0  
/dev/sdd1                                  /media/W2003Server  ext3         errors=remount-ro      0  0  
/dev/sdd2                                  /media/TestSpace    ext4         defaults               0  0  

```

Thx.

David

---

### Post by olddave1 on 2011-11-28
Anyone?

To me looks like the live Cd is not really setup for this sort of transfer from one disk to a new disk. I have not found a tutorial that is to the point on this subject.

thx.

David

---

### Post by oldfred on 2011-11-28
I do not know RAID nor LVM. But the install would be a lot different, so I do not think it would be easy to copy. I would suggest the clean install and copy some or all of /home over.

I just purchased a SSD and created gpt partitions and did a standard install. I always keep /home in my /, but have all data on my other drives in /mnt/data or /mnt/shared which I then link into /home. So my /home is just my user settings and some hidden folders. /home also includes my .wine as that is more difficult to move to a data partition.

With RAID & LVM you have to use the alternative install CD to have the drivers for RAID & LVM.

Also for installing on fakeraid (motherboard raid), this might help you:
[https://help.ubuntu.com/community/FakeRaid](https://help.ubuntu.com/community/FakeRaid)
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

I am not a fan of RAID for most desktops. I believe just using a SSD provides the extra speed one might want if compiling or other hard drive intensive uses. RAID is not a replacement for backups and in some cases makes backups even more important as a failure of one drive destroys the entire RAID.

---

### Post by olddave1 on 2011-11-28
I am not sure I am using fakeraid, the article mimics RAID using LVM, because TRIM does not work with fakeraid. Or is it just the RAID1 that uses fake raid and doesn't need TRIM because it is read only effectively

Could I do some sort of low level copy of my current /boot to the 'RAID1' SSD and the rest to the 'RAID0' (LVM) /?

I should point out that the SSDs have their RAID/LVM already setup as can be seen in the top 2 commented out lines of my fstab.

Thx.

David

---

### Post by darkod on 2011-11-28
From what I can see in the link you provided in your first post, that's only raid1 for /boot and LVM for /, not raid0.

Look more carefully in the steps towards the middle of the article, when he's setting it up. It clearly says raid1 for /boot, and then it just says LVM for /, no mention of raid0.

His fdisk results say it all, partitions #1 are raid autodetect, partitions #2 are lvm. For raid0 partitions #2 would also be raid autodetect, and the lvm sits on top of the raid. First you create the raid as physical device, and then use that physical device for lvm.

I don't know if this will make you rethink your setup or should we continue? At the moment I don't think you will be writing to both SSDs at the same time thus gaining speed. I assume speed was your point for raid0 because you don't get any redundancy with it, just risks.

PS. That article uses software raid, not fakeraid. /dev/mdX is software raid, fakeraid looks like /dev/mapper/blabla

PPS. LVM also uses /dev/mapper/blabla but that's different compared to fakeraid.

---

### Post by olddave1 on 2011-11-28
Hi,

This is what attrached me "The solution is to create 2 physical volumes out of the SSDs, and create an LVM stripe over them (or mirror if you want RAID1). That will work just like a RAID0, but TRIM will work this time!" I assume he means it will perform like RAID0 otherwise what is the point...

I suppose the question is, can I setup Unbuntu on my SSDs setup like this, He seems to to be suggesting that the install is straightforward here:
"You are ready to install now, just remember to not format the partitions again in the installer"
and
"Add noatime and discard (required for TRIM support) mount options to /etc/fstab:"

But with a Live CD it did not seem to give me the option of placing my install on these existing drives (I had uncommented them in fstab), so unless the install can somehow 'import' that fstab it is not at all clear how you do an install?

So in answer to your question, RAID1 important for boot and RAID 0 or equivalent very important for the  10 hours a day I spend developing software.

Thx

David

---

### Post by darkod on 2011-11-28
I don't have some in depth LVM knowledge, but I think the author is comparing lvm to raid0 very loosely.
My logic (which can be wrong):
raid0 writes to both disks at the same time, thus in effect doubling the transfer rate. This is its purpose, not redundancy which it hasn't got.
LVMs purpose is to allow easily expanding and adding physical volumes (disks) to an existing system without the need to reformat your partitions. It was not meant to write to both disks at the same time. Sometimes it might, but not always. While for raid0 always writing to both disks is a rule. EDIT: That is why for example you can have lvm of three disks, but not raid0 of three disks. Also, you can add partitions of different size to lvm but for raid0 you need them to be equal.

Maybe someone else will jump in and help clarify this.

Since you seem to be doing a new install, how is this for an idea:
Get the alternate install cd, not the standard desktop cd (for raid and/or lvm you should use the alternate anyway).
Start the install. At the partitioning step select manual.
Delete all the partitions on both disks. Create equal partitions for /boot on both disks and select raid type.
Then create the equal partitions for / but select lvm type.
Above the partitions list you have the software raid and lvm options.
Select Configure software raid. Configure a raid1 array of sda1 and sdb1. That will show as new device in the partitions list.
Select Configure LVM. Select the physical devices sda2 and sdb2, create the volume group and the logical volume. In fact, it's the same like that link only you are doing it with the installer, not in terminal after that. The LVM will also show as separate device in the partitions list.

Select the raid device, create new primary partition on the whole device, select /boot mount point, ext4 filesystem.
Select the lvm device, create new primary partition on it, mount point /, ext4,

That's it. You have your new system. Copy the parts from the old /home that you want, and also other data.

I still think the LVM will not do the job you think it will. But I will say again, I might be wrong.

---

### Post by olddave1 on 2011-11-29
The point here is that LVM striped provides most of the performance of RAID0 and allows the use of TRIM which RAID0 does not. [http://www.linux-mag.com/id/7582/2/](http://www.linux-mag.com/id/7582/2/)

I'll try the new Install this weekend.

Thx.

David

---

### Post by darkod on 2011-11-29
Yeah, after you got me curious I also started googling around. It seems you can set up LVM for striping which should give you similar performance to raid0.

I haven't used it so I can't say anything. :)

---

### Post by olddave1 on 2012-04-24
Hi,

Reviving this again, because I never succeeded in getting my SSD's in RAID1 for boot and LVM striped for / working. And now the 2nd hard drive of the rotating kind is failing. 

So, how can I use Live CD to setup Xubuntu 11.10 on the SSDs and then copy across my entire install from my old HDD, (now with errors fixed).

The part that I do not get is when I do a fdisk -l running from liveCD it shows the /dev/sda1 and /dev/sdb1 as having start block of 1 and end block 117231407 and saying that as these are GPT and that I should use GNU Parted. Where would I see the /dev/mapper/vgssd-lvssd and /dev/md0?

Once I 'see' these I assume I mount them? Then once mounted I can ddrescue to clone the /boot to the /dev/md0 and / to the /dev/mapper/vgssd-lvssd? Is that the right approach? Do I then somehow get grub to boot from /dev/md0?

Thx.

David

---

### Post by darkod on 2012-04-24
In live mode you will need to install mdadm and lvm2 to be able to read software raid arrays and LVM devices.
sudo apt-get install mdadm lvm2

Look here for detailed instructions to mount LVM from live mode:
[http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/](http://quonn.wordpress.com/2010/12/01/how-to-mount-lvm-partition-on-ubuntu/)

If I am not mistaken, the /dev/md0 should be readable after you install mdadm without further actions. If it's not, maybe you will need to tell it to assemble, but be careful not to use the --create option with mdadm. You only use that once when the array is created. If you do it again it will destroy the current array and create a new blank one.

So, you want to copy everything over to new partitions? I am not sure how ddrescue is working, but dd copies sector by sector so I would not use that actually. It will keep copying empty sectors too.

You can look into using cp with some options to include all hidden files, etc. Or making a backup first onto some kind of external hdd, and then restoring that backup to the new hdds/ssds. One option for this backup is FS Archiver for example.
[http://www.fsarchiver.org/Main_Page](http://www.fsarchiver.org/Main_Page)

---

### Post by olddave1 on 2012-04-24
Hi,

I ran GParted from the LiveCD. It shows me that I have sda1 as filesystem unknown 1MB hand with theh bios_grub flag, sda2 as ext3 242MB and sda3 as lvm2 and 55.66GB. Identical for sdb. GParted shows for sda1 and sdb1 both warn that it is unable to detect a file system, is this because it is soft raid 0?

I tried to mount /dev/md0 and it tells me it does not exist. I was going to try sudo cp -ax /media/old-partition /media/new-partition for /boot but since I cannot mount /dev/md0 that is kinda impossible.

Any suggestions?

David

---

### Post by olddave1 on 2012-04-24
Thx, installed lvm and activated the LVM volume and mounted it as /mnt. The problem I hav enow is that how do I mount my old disk on /dev/sdc? I tried "sudo mount /dev/sdc /" but of course the LiveCD is mounted there?

Secondly, /dev/md0 is NOT recognised, how do I set that up again?

Unclear what to mount things as because there are reserved names like '/mnt' and '/', you cannot just use any old name. So what names do you mount the 2nd drive on to be able to cp -ax from one to the other?

---

### Post by darkod on 2012-04-24
You can create folders in /media. Of course, being in live mode this is just temporarily, but enough to finish the job. For example:
sudo mkdir /media/oldroot
sudo mkdir /media/newroot
etc

Then you mount there and start the copy. Do not try to use / or similar as mount point. Use temporary mount points just to do the copy.

As far as mdadm is concerned, if the array is still OK you should be able to assemble it with:
sudo mdadm --assemble --scan

That will scan for the devices and assemble all arrays it can find.

---

### Post by olddave1 on 2012-04-24
OK, getting further. I managed to get /dev/mdo started by doing this "sudo --assemble --scan" then mount it  using "sudo mount /dev/md0 /boot"

Not I just need to work out how to mount the old partitions for / and /boot from my old hard drive, but cannot work out what mount names to use?

David

---

### Post by darkod on 2012-04-24
> **olddave1 said:**
> OK, getting further. I managed to get /dev/mdo started by doing this "sudo --assemble --scan" then mount it  using "sudo mount /dev/md0 /boot"

Not I just need to work out how to mount the old partitions for / and /boot from my old hard drive, but cannot work out what mount names to use?

David

DO NOT use / and /boot as mount points. You are simply trying to do a copy operation, not to run a system. Avoid the "real" mount points to avoid any problems.

---

### Post by olddave1 on 2012-04-24
Thx, the mkdir works perfectly, and our messages passed each other for the mdadm assemble. 

So while it is copying things (it'll take a while) once I have / on /dev/vgssd/lvssd I need to install grub on I assume both /sda1 and /sdb1? Not too sure about /boot though, as it is currently under /. So I assume I can just copy from /media/newroot/boot to a new mount , lets call it /media/newboot? Then reboot and all will be good?

David

---

### Post by darkod on 2012-04-24
You will need to install grub2 on both /dev/sda and /dev/sdb I guess, not sda1 and sdb1, not the partitions.

So, currently /boot is inside / and you want it to be separate on the new install?

Yeah, just copy /media/newroot/boot into /media/newboot. I am not sure if leaving the original files in /media/newroot/boot might interfere because you will have separate /boot partition and a boot folder inside /. There might be a conflict, so you might need to delete it after you copy the files to newboot.

After you finish the copy, unmount all temporary mounts and the installation of grub2 would go like:
sudo mount /dev/mapper/vgssd-lvssd /mnt
sudo mount /dev/md0 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sda
sudo grub-install --boot-directory=/mnt/boot /dev/sdb

Since you are moving into a very different setup, you might need to enter the new partition with chroot, purge the grub2, and reinstall it. I can't be 100% just adding grub2 to the MBR of the disks will do the job because it has the UUIDs of the old partitions inside its config files.

---

### Post by olddave1 on 2012-04-24
Well, based on the performance so far it is copying 1.9GB/hour with 63GB to go I will be back on Thursday to complete this. 

I tried this

sudo dd if=/dev/sdc of=/dev/vgssd/lvssd bs=10M conv=notrunc

I Ctrl-C to see theh speed and it is doing 6.1MB/s not fast but better than before

---

### Post by oldfred on 2012-04-24
If you are copying with dd from MBR to gpt you may have issues.

See this thread and post #12 by srs5694 who is the author of gdisk and knows gpt very well.
Do not use dd to copy drive with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)

---

### Post by olddave1 on 2012-04-26
Well, what crap.

The dd took 35 hours and failed due to lack of space. Because the partition size was larger but I had not realised that I needed to dd from /dev/sdc1 not from /dev/sdc.

So since I had a better understanding and I had a 1MB bios_flag partition, a 254MB /dev/md0 for /boot and /dev/vgssd/lvssd for / I figure the manual install option should work, and it appeared to work. But on reboot my /dev/md0 and my /dev/vgsssd/lvssd are gone, the installer somehow destroyed them. Back to square one. No real work done for 2 days now. You'd think with SSDs so popular and the logical setup of a RAID1 /boot and a fast LVM striped would be so demanded that the installer would support it.

Not sure what my next step is. Cannot bear starting from scratch again without knowing there is a clear way of getting to the fast reliable machine I want. Might be time to spend £80 on Windows 7?

---

### Post by darkod on 2012-04-26
Are you sure they are gone or just not activated?

Are you using the liveCD installer or the alternate installer?

---

### Post by olddave1 on 2012-04-26
I realise I am completely out of my depth here. I did "sudo ls /dev" to check if /dev/vgssd was there, and it definitely was NOT. I also use the Install alternate to see the partitions, they were NOT there. The I checked for /dev/md0 and it was not, so started the whole process in that original post on OCZ forum again. 

I did the 
# mdadm --create --verbose /dev/md0 --level=mirror --raid-devices=2 --metadata=0.90 /dev/sda1 /dev/sdb1
# mkfs.ext3 /dev/md0

Moved onto the pvcreate, no problem, then the vgcreate, it tells me that the "/dev/vgssd already exists in filesystem" Huh? Then I went back into the Ubuntu alternate install (it is the only way I know how to see the partitions because GPArted cannot support GPT or something) and this time it lists the /dev/vgssd and the /dev/md0, but now the /dev/md0 is 0 bytes and has no partition. 

Seems somehow it did not show these devices and now it is and my actions to try to recreate have left me in no mans land. Cannot see how he created that 254MB partition on /dev/md0. Which of his steps here 
[http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux&highlight=olddave](http://www.ocztechnologyforum.com/forum/showthread.php?82648-software-RAID-LVM-TRIM-support-on-Linux&highlight=olddave)
created that 254MB partiton, or how do I get it setup that way?

Thx.

David

---

### Post by darkod on 2012-04-26
Don't forget what we mentioned earlier. To read software raid and LVM in live mode, you need to install the mdadm and lvm2 in live mode, and activate them.

He created the boot partition with those two commands you wrote yourself in the last post.
The mdadm --create creates the /dev/md0 raid device, and the mkfs creates the ext3 (or ext4 if you prefer) filesystem on it.
Note that mdadm --create is used only the fist time, later to only activate a device you can do mdadm --assemble --scan.

For only listing existing partition you can depend on parted, it reads both msdos and gpt without issues. For example:
sudo parted /dev/md0 print all

will print the partitions for all devices, not only /dev/md0. If you run it without the 'all' it will print them only for the device you specify.

That tutorial doesn't mention one important thing that I am not sure about.

It starts with the liveCD so you can create the partitions first. But the liveCD doesn't have built in support for mdadm and lvm2. Yes, you can add them to manipulate the devices, but when you continue and finish the install with the liveCD, are mdadm and lvm2 included in the installed OS?
That is the main question that the tutorial doesn't touch. Are they there by default because in the standard liveCD installation they are not. And if they are not there, there is nothing to "translate" /dev/md0 and /dev/mapper/vgssd-lvssd to the OS.

It's possible that after the install you might actually need to chroot into the / and install mdadm and lvm2 and make sure they are loaded on boot.

So, do you want to remove the existing LVM or continue trying with it? You can simply format it again without removing it, that should delete any data on it and you start clean. To activate the LVM you have that link I gave you few posts ago (I don't have it right now).

---

### Post by olddave1 on 2012-04-26
My /dev/mdo is 960 blocks much smaller than it was the 1st time I did it.

I just use apt-get for mdadm and lvm2.

I think that I can leave /dev/vgssd/lvssd alone, assuming my pvcreate did not destroy anything, and just try to get /boot back onto a 254MB /dev/md0. So I need to streaatch the /dev/md0 to be 254MB as it was, I assume to the start block of the /dev/vgssd.

Here is sudo parted /dev/md0 print all

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   117231407    58615703+  ee  GPT
ubuntu@ubuntu:~$ sudo vgcreate vgssd /dev/sda2 /dev/sdb2
  /dev/vgssd: already exists in filesystem
  New volume group name "vgssd" is invalid
  Run `vgcreate --help' for more information.
ubuntu@ubuntu:~$ sudo mdadm --detail /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Thu Apr 26 09:35:14 2012
     Raid Level : raid1
     Array Size : 960
  Used Dev Size : 960
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Thu Apr 26 09:40:08 2012
          State : clean
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : e4005531:c882ea69:e368bf24:bd0fce41 (local to host ubuntu)
         Events : 0.17

    Number   Major   Minor   RaidDevice State
       0       8        1        0      active sync   /dev/sda1
       1       8       17        1      active sync   /dev/sdb1
ubuntu@ubuntu:~$ sudo /proc/mdstat
sudo: /proc/mdstat: command not found
ubuntu@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 sdb1[1] sda1[0]
      960 blocks [2/2] [UU]
      
unused devices: <none>
ubuntu@ubuntu:~$ sudo parted /dev/md0 print all
Model: Linux Software RAID Array (md)
Disk /dev/md0: 983kB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  983kB  983kB  ext2


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB  ext2                   bios_grub
 2      2097kB  256MB   254MB                          boot
 3      256MB   60.0GB  59.8GB               extended


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB  ext2                   bios_grub
 2      2097kB  256MB   254MB                extended
 3      256MB   60.0GB  59.8GB               extended


Model: ATA SAMSUNG SP2004C (scsi)
Disk /dev/sdc: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  119GB  119GB   primary   ext4            boot
 2      119GB   127GB  7999MB  extended
 5      119GB   127GB  7999MB  logical   linux-swap(v1)


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size   File system  Name         Flags
 1      17.4kB  603GB   603GB  ext3         W2003Server
 2      603GB   1000GB  397GB  ext4         Partition1   lvm


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/vgssd-lvssd: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      262kB  120GB  120GB  primary  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

---

### Post by darkod on 2012-04-26
One question slightly off topic: why do you use gpt? You only need that for huge disks, the SSDs can work with msdos just fine.

Unless thee is a reason unknown to me. It seems to me it would be easier with msdos table.

---

### Post by darkod on 2012-04-26
Look at this:
> ubuntu@ubuntu:~$ sudo cat /proc/mdstat
Personalities : [raid1] 
md0 : active raid1 [COLOR=Red]sdb1[1] sda1[0][/COLOR]
      960 blocks [2/2] [UU]
      
unused devices: <none>
ubuntu@ubuntu:~$ sudo parted /dev/md0 print all
Model: Linux Software RAID Array (md)
Disk /dev/md0: 983kB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  983kB  983kB  ext2


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 [COLOR=Red]1      1049kB  2097kB  1049kB  ext2                   bios_grub[/COLOR]
 2      2097kB  256MB   254MB                          boot
 3      256MB   60.0GB  59.8GB               extendedYour md0 is assembled from sda1 and sdb1, but because of the gpt table and the small bios_grub partition created for gpt disks, the partitions you planned to use for boot is sda2/sdb2 not sda1/sdb1.
That's why your md0 is barely 1MB instead of 254MB.

As mentioned above, msdos doesn't use bios_grub so it would be easier, unless you have a good reason for gpt.

---

### Post by olddave1 on 2012-04-26
bios_grub is required, because Grub2 does not fit in MBR anymore and you need this little partition to put it in.

You have discovered my mistake. I need to have sdb1 and sda1 as the place to put Grub2 and sdb2 and sda2 for my /dev/md0 for /boot. Now how to get to that point...

---

### Post by darkod on 2012-04-26
I understand about bios_grub if you use gpt. That's why I said, if you use msdos tables you don't need that small partition, one partition less. It is only needed for gpt table, not for msdos.

Can this help you in removing the /dev/md0 and after that you can create it again with sda2/sdb2:
[http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html](http://www.tcpdump.com/kb/os/linux/removing-raid-devices.html)

---

### Post by olddave1 on 2012-04-26
I mentioned I am using alternate. 

fortunately because I was out by one the pvcreate did not touch my /dev/vgssd. I have recreated /dev/md0 on dev/sda2 and /dev/sdb2 . Now I need to work out how to setup /dev/sda1 and /dev/sdb1 with the grub2

But I am a little confused as to why now parted shows this, sda1 sda2 ans sda3 should be showing?
ubuntu@ubuntu:~$ sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   117231407    58615703+  ee  GPT

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1   117231407    58615703+  ee  GPT

Disk /dev/sdc: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b60fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048   232421375   116209664   83  Linux
/dev/sdc2       232423422   248045567     7811073    5  Extended
/dev/sdc5       232423424   248045567     7811072   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1  1953525167   976762583+  ee  GPT

Disk /dev/mapper/vgssd-lvssd: 119.5 GB, 119529275392 bytes
255 heads, 63 sectors/track, 14531 cylinders, total 233455616 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 262144 bytes
Disk identifier: 0x000212e1

                  Device Boot      Start         End      Blocks   Id  System
/dev/mapper/vgssd-lvssd1             512   233455103   116727296   83  Linux

Disk /dev/md0: 253 MB, 253689856 bytes
2 heads, 4 sectors/track, 61936 cylinders, total 495488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table

---

### Post by darkod on 2012-04-26
fdisk does not show gpt correctly. It shows it as a single gpt partition spanning the whole disk.

That's why use parted to print the partitions layout on gpt disks. You can also use it to create/delete partitions, create partition tables, etc.

---

### Post by olddave1 on 2012-04-26
I ended up with the parted output below after building the /dev/md0 on /dev/sda2 and /dev/sdb2 and removing the raid1 on sda1 and sdb1. From my reading of GRUB2 it will find the sda1 with the bios_grub flag and use it. 

ubuntu@ubuntu:~$ sudo parted /dev/md0 print all
Model: Linux Software RAID Array (md)
Disk /dev/md0: 254MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  254MB  254MB  ext3


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sda: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB  ext2                   bios_grub
 2      2097kB  256MB   254MB                          boot
 3      256MB   60.0GB  59.8GB               extended


Model: ATA OCZ-VERTEX2 (scsi)
Disk /dev/sdb: 60.0GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name      Flags
 1      1049kB  2097kB  1049kB  ext2                   bios_grub
 2      2097kB  256MB   254MB                extended
 3      256MB   60.0GB  59.8GB               extended


Model: ATA SAMSUNG SP2004C (scsi)
Disk /dev/sdc: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  119GB  119GB   primary   ext4            boot
 2      119GB   127GB  7999MB  extended
 5      119GB   127GB  7999MB  logical   linux-swap(v1)


Model: ATA SAMSUNG HD103SJ (scsi)
Disk /dev/sdd: 1000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size   File system  Name         Flags
 1      17.4kB  603GB   603GB  ext3         W2003Server
 2      603GB   1000GB  397GB  ext4         Partition1   lvm


Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/vgssd-lvssd: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start  End    Size   Type     File system  Flags
 1      262kB  120GB  120GB  primary  ext4


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

This all looks good, but I did an install and it hangs at the point it says "Saving installed packages". So once again stuck. Any ideas on next steps?

My plan was a fresh install then boot on the alternate CD and mount my old ~ and the new ~ and do an rsync to get all my old goodies across. Any flaws in that plan if I even get to the point of a bootable system?

Thx

---

### Post by olddave1 on 2012-04-26
I should also say the install stalled with the message in the little window under the "Saving installed packages..." 
'Apr 26 16:56:33 ubuntu ubiquity[25587]: log-output -t ubiquity laptop-detect'

Now 18:51 so I assume it ain't going anywhere at this stage. The Skip button is not activated.  The install has no cancel button either, so I assume I have to kill the process?

---

### Post by darkod on 2012-04-26
I have no idea about that error.

But I have noticed that you made the bios_grub partition ext2. It should be without a filesystem, just a partition. I am not sure if it will work with ext2.

The best tool for creating a partition without a filesystem is parted because it creates only the partition and you add the filesystem later. If you don't do that it will be left without one.

---

### Post by olddave1 on 2012-04-26
Hi,

I killed the install process. I gparted and removed the /dev/sda1 and /dev/sdb1 partitions. I recreated the partitions, this time not formatted and also set the bios_grub flag on both.

I restarted the install, it stalled at the step after the last time -
'Apr 26 19:08:35 ubuntu ubiquity[19034]: log-output -t ubiquity fontconfig-vood' (this might be clipped by their small window, poor design) 
'--auto -- force --quiet'

Any Ubuntu folk know what the hell is going on?

---

### Post by darkod on 2012-04-26
Sorry, I have no clue.

This topic got me so interested that I am doing a virtual box test right now. I didn't try to stripe the LVM, I only create one single sda1 physical device and two LVs for root and /home.
So far the install with the liveCD is going as expected. Lets see after it finishes and after the first reboot.

---

### Post by olddave1 on 2012-04-29
As mentioned in my other thread, your method of using grub-install ended up with a grub> prompt only. 

In the end I 'borrowed' as new hard drive destined for my wife's PC. dd across from my failing old spinning disk. Ran boot-repair and booted. Then booted from LiveCD, ran fsck to fix the errors and it boots and runs. So Ubuntu simply goes not support SSDs in a reasonable configuration is the only conclusion I can come to. 

Darkod is the only one who seems to have the knowledge to tackle this which seems amazing to me, thanks. I know someone who said that Arch Linux has a much better forum for supporting these sorts of issues, when I get a chance will try that.

Cheers,

David

---

