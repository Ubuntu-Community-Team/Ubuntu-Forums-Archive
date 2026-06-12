---
title: "Partitioning in GPT"
date: 2014-08-22
forum: Installation &amp; Upgrades
---

### Post by LaughingHorse on 2014-08-22
I had a post about my desktop disappearing, not being able to print, etc.
The situation ended up getting much worse, where the desktop bar at the top dissapeared. I believe it was due to compiz - which after thinking about I had a look at to see what it would do. Did not change anything and then everything went crazy.

Ayway, it seemed like there was no other way to go than to do a complete install on sdb and overwrite everything. So I did.

Fortunately, I had a backup of almost everything. I missed one document I had created, and can re-create that one.

I let the install disc create the partitions.

Fortunately, or unfortunately it created it in BIOS rather than MBR.

Here are my questions:

1. From reading I found I can not create Extended and Logical partitions since the partition tables are now GPT I do want a seperate partition for the Ubuntu system, and one for my data.

And I read that since the partitions are GPT I can create many more than 4 primary partitions. So would I be best off making Partition 2 GB and making a big partition 3 for home and data? 

If I do that, do I need to once again re-install 14.04?
as in thread [http://ubuntuforums.org/showthread.php?t=2239906](http://ubuntuforums.org/showthread.php?t=2239906)

Looking at the partitions on sdb the first one is FAT32 and the installation set it up as the boot with mount point being /boot/efi 

Here is what my disks look like as currently partitioned.

sudo fdisk -l

```

Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd7329376

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          206848    48383999    24088576   1b  Hidden W95 FAT32
/dev/sda3        48384000  1611192319   781404160    7  HPFS/NTFS/exFAT
/dev/sda4      1611192366  3907024064  1147915849+   7  HPFS/NTFS/exFAT
Partition 4 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 390702916  sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  3907029167  1953514583+  ee  GPT

```

I searched and found the code to display the partitions on sdb
sudo parted /dev/sdb print
```

Model: ATA WDC WD2002FAEX-0 (scsi)
Disk /dev/sdb: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot
 2      538MB   1419GB  1419GB  ext4
 3      1965GB  2000GB  35.0GB  linux-swap(v1)


```


mount

```

/dev/sdb2 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /sys/firmware/efi/efivars type efivarfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sdb1 on /boot/efi type vfat (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=allen)
/dev/sdg1 on /media/allen/My Passport type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)

```

Note: when I ran the mount command I was in the process of transferring backup files from mypassport to my hdd

---

### Post by oldfred on 2014-08-22
I posted in your other thread on UEFI install on sdb.
Some like just using one time boot key to dual boot when installed in different boot modes. Others want all systems in same boot mode.

You do not have to reinstall, but moving /home is a bit more complex. If a total new user reinstall may be easier, but moving /home can be a learning experience. :)
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But I prefer to have /mnt/data for all my data. I also still have a /mnt/shared which is NTFS for sharing with my XP install which now is not used. All new data goes into my /mnt/data and next time I reconfigure the NTFS partition will disappear. I keep /home inside / (root), but it is only 2GB and 1.5GB of that is .wine for Picasa. Or hidden user settings are tiny. I also move larger hidden data folders like the Firefox & Thunderbird profiles to my data partitions for sharing, so not many folders that are large are in my /home.

With added partitions you can just click on them with Nautilus and they will automount. But if internal drive you really want them automounted when you reboot. With Linux you have to give it a name or mount point. One advantage of Linux is that you can use names that mean something to your rather than Window's use of d: or e:
And you have to edit fstab to tell system which partition to mount to which mount point you created.

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
            Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

    If you just want new partition(s), you can use gparted to shrink your Linux partition and create new partition(s).

---

### Post by LaughingHorse on 2014-08-22
Thank you oldfred!

Since these are two seperate issues I thought it better for others to open two threads. Even though they are somewhat related :)

It looks like it will be much faster to move the home folder.
It looks like the link you gave me here
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

makes it pretty easy.

Looks like it is basically just copy and paste... then wait :)

And it look slike I will have to make the new partition at least as big as the current partition for Ubuntu so i can copy the files I backed up to that one.
Then later adjust the partition down to around 30 GB 

Does that sound about right, or am I missing anything?

Sitll confused about the partitioning, and will post that question in the partitioning thread I started.

The good news is since I've installed 14.04 about 10 times now over the past week on my computer... I'm really comfortble with the process :)
Just don't want to go though all the time and, effort again.

---

### Post by oldfred on 2014-08-22
You also are manually editing fstab to add an entry for /home.

Even 30GB for / is generous unless planning on lots of games and having those in /.
I create 20 or 25GB root partitions. 
I have /home inside / and it is about 2GB with 1.5GB of that as .wine.
My 12.04 install used 11GB including the /home.
My 14.04 is now 7.4GB, but I have not quite reinstalled everything yet. 
I think most of difference was logs & other accumulation that even some light housecleaning does not remove.

---

### Post by LaughingHorse on 2014-08-22
I started following the instructions in the link.

and Here is what I did so fara, but have a question before actually making the change:
```

/dev/sdb1: UUID="DA1D-92DC" TYPE="vfat" 
/dev/sdb2: LABEL="Ubuntu 14.04" UUID="3091b06d-9431-4211-9be3-b7235ba8fe39" TYPE="ext4" 
/dev/sdb3: UUID="d3edb072-8a5e-491a-9ff0-78d357806f10" TYPE="swap" 
/dev/sdb4: LABEL="home" UUID="c7f395e4-3b68-41f9-a705-a37eb366eed2" TYPE="ext4" 

```
The partition I've have set to be the new /home partition is sdb4

I used the code to Duplicate the fstab file
```

sudo cp /etc/fstab /etc/fstab.$(date +%Y-%m-%d)

```

I checked and thye were the same

Open the original fstab in gedit:
```

gksu gedit /etc/fstab 

```

and added these lines into it 
```

# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)  
UUID=c7f395e4-3b68-41f9-a705-a37eb366eed2   /media/home    ext4          defaults       0       2 

```
I don't understand what is meant under "defaults 0 2"
Would this be correct for my system, or do i need to change something?

---

### Post by oldfred on 2014-08-22
See this for details:
man fstab

Since it is a temporary mount it is not critical on settings, but you have to have all fields with settings.

---

### Post by LaughingHorse on 2014-08-22
So the "defaults 0 2" is basically just filler then?

---

### Post by oldfred on 2014-08-22
Not really, they all are required. And mount options vary a lot depending on format and use of partition.
And the last digit determines whether fsck is run or not. Since you cannot run fsck on NTFS partitions then that setting is different also if mounting a NTFS data partition.

Link should have the standard settings for  a /home partition.

---

### Post by LaughingHorse on 2014-08-22
Since the instructions said to add and not delete the lines
# (identifier)  (location, eg sda5)   (format, eg ext3 or ext4)      (some settings)  
UUID=c7f395e4-3b68-41f9-a705-a37eb366eed2   /media/home    ext4          defaults       0       2 

After the transfer is done and tested to make sure it is complete,
would I delete the old line out of fstab?

---

### Post by oldfred on 2014-08-22
Yes, but then you add the correct fstab entry for /home, not a /media/home. That converts from using the internal to / (root) /home to using the new partition. 
Should be ub the the last set of instructions. 
Example shows ext3, but I assume you use ext4 now and of course the UUID of your new /home partition.

---

### Post by LaughingHorse on 2014-08-22
Yes, later on there will be the changing from /media/home to /home.
 But the instructions did not say to replace the original line, just to add the new one.
So my concern is the system gets hung up looking for a home that does not exist, or will it be just loading Ubuntu, and the additional extension with home if the old line is left as it is?

---

### Post by oldfred on 2014-08-22
The instructions say to edit the temporary mount with a permanent setting. 
You are just changing /media/home to /home.
But then have to get system to switch. 
Instructions have changing from old /home inside / to new /home mounted via fstab without rebooting. But once fstab is correctly changed to mount the new partition that is /home then every reboot should mount it.

---

### Post by LaughingHorse on 2014-08-23
oldfred, I'm sure you were waiting with baited breath to hear the results.

Everything worked out perfectly!
I followed the instructions from that link you gave me
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
And there were absolutely no issues, with the exception of my questions to you and needing reassurance of what should happen.

What I learned:
1. Make a Backup. It will save your...
2. Before switching the home directory, do yourself a favor and delete ALL the data you can. It's already backed up. 
I made the mistake of not deleting the data, so it took a lot longer than necessary.
All night long my hard drive was thrashing trying to compare what I moved against what the original was.

I could have saved a lot of wear and tear on the hard drive had I deleted all the files and just left the packages and Ubuntu.
And the deletion includes the folder for Thunderbird holding emails. That can be restored after the move.

3. After the move was successful, I then used the install disc and used gparted to reduce the partition holding Ubuntu, and add that to the partition /home
It would have been a lot faster had I deleted the data files (music, pictures, email folders, etc) BEFORE doing this.
A lesson to me :)

And here is a picture of my newly partitioned and newly moved /home directory.

[ATTACH=CONFIG]255769[/ATTACH]

So I will mark this thread as solved.

oldfred, I can not thank you enough!

So a big THANK YOU!!!!!!! will have to do.

---

### Post by oldfred on 2014-08-23
Glad that worked. :)

---

