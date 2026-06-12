---
title: "Reduced home disk space"
date: 2012-07-31
forum: Installation &amp; Upgrades
---

### Post by scratchesheadinvain on 2012-07-31
**EDIT: problem solved but beginner questions remain. Feel free to continue to comment. Thanks in advance**

Hi All,

I have been using Ubuntu for a couple of months now but I still have no clue as to how it works. I've broken it more times than I care to say.

My latest problem has me perplexed and I do not want to have to reinstall _again_! (Unless I absolutely have to).

So I recently made the move from 11.10 to 12.04. I done so by using the option from the boot image which says something like 'delete previous installation of ubuntu and install 12.04'. When the installation was complete, my home directory is only ~30GB's and I have a ~480GB file-system showing up in /media.

I'd really like these two to be merged. From looking around I see that the following might be helpful

> 
dbyrne@Leslie:~$ ls -l /dev/disk/by-uuid/
total 0
lrwxrwxrwx 1 root root 10 Jul 31 12:53 3030-3030 -> ../../sda1
lrwxrwxrwx 1 root root 10 Jul 31 12:53 80229593-cabe-419c-b234-c74289249a18 -> ../../sda5
lrwxrwxrwx 1 root root 10 Jul 31 12:53 a1bdd362-43d4-40a3-af01-7c2d1b04df9d -> ../../sda6
lrwxrwxrwx 1 root root 10 Jul 31 12:53 C022622022621BA2 -> ../../sda2
lrwxrwxrwx 1 root root 10 Jul 31 12:53 E4C43F7EC43F51D2 -> ../../sda3
lrwxrwxrwx 1 root root 10 Jul 31 12:53 e906cefb-319f-4ea7-a03d-938a800445e5 -> ../../sda7

dbyrne@Leslie:/media$ sudo fdisk -l
[sudo] password for dbyrne: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *      212992    41172991    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41172992   447696429   203261719    7  HPFS/NTFS/exFAT
/dev/sda4       447696894  1465147391   508725249    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       508119040   523742085     7811523   82  Linux swap / Solaris
/dev/sda6       523743232  1465147391   470702080   83  Linux
/dev/sda7       447696896   508119039    30211072   83  Linux

Partition table entries are not in disk order

dbyrne@Leslie:/media$ sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="3030-3030" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="C022622022621BA2" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="E4C43F7EC43F51D2" TYPE="ntfs" 
/dev/sda5: UUID="80229593-cabe-419c-b234-c74289249a18" TYPE="swap" 
/dev/sda6: UUID="a1bdd362-43d4-40a3-af01-7c2d1b04df9d" TYPE="ext4" 
/dev/sda7: UUID="e906cefb-319f-4ea7-a03d-938a800445e5" TYPE="ext4"

and my fstab is as follows:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e906cefb-319f-4ea7-a03d-938a800445e5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80229593-cabe-419c-b234-c74289249a18 none            swap    sw              0       0

a1bdd362-43d4-40a3-af01-7c2d1b04df9d on sda6 is the ~480GB drive that has been separated.

Any and all help is very much appreciated. I should also add, this machine is dual booted with windows and I doubt its having an effect now but is running nvidia graphics which is causing me all sorts of problems elsewhere. 

Thanks,
D

---

### Post by darkod on 2012-07-31
If you look carefully in fstab you will see that sda7 is the root partition, hence it can't be the "separated" one. Look into the mounted partition and you should see sda7 mounted as /:
df -h

So, actually sda6 looks like the partition you are not using right now. Did you have a separate /home partition previously? I don't think any of the automated install methods can handle separate /home, you have to install with the manual partitioning for that.

---

### Post by scratchesheadinvain on 2012-07-31
Hi darkod,

Your completely right, sorry, not sure why I said sda7. Must have gotten confused. I'll edit the main post.

> dbyrne@Leslie:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        29G  8.7G   19G  32% /
udev            3.9G  8.0K  3.9G   1% /dev
tmpfs           1.6G  912K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  484K  3.9G   1% /run/shm
/dev/sda3       194G   54G  141G  28% /media/OS
/dev/sda6       449G   12G  415G   3% /media/a1bdd362-43d4-40a3-af01-7c2d1b04df9d
To be honest, I don't remember having a separate /home partition previously (bar separating from the OS partition) and I can't think of a reason why I would have. Its certainly possible but it definitely wasn't only ~30Gb's.

---

### Post by darkod on 2012-07-31
Well, what is done is done. If you don't wanna reinstall you can create a mount point for sda6, something like /media/data for example.
Then you will need to add an entry in fstab so that sda6 is always mounted at /media/data at boot.
After that the 415GB will be available in /media/data.

Another option is to make sda6 a separate /home partition. You can do that without reinstalling. First you will need to copy the content of the current /home but I'm not sure how to do that in a best way so that all permissions are kept. If oldfred reads this he might jump in, he knows more.
After the copy, you create the entry in fstab mounting sda6 as /home. After a reboot ubuntu will consider it your "new home" partition.

---

### Post by scratchesheadinvain on 2012-07-31
This is a great idea. Thanks darkod. This will certainly sort out my problem...I think...I may have to change some dependencies but sure thats a better option then reinstalling. Thanks again.

For sake of interest and learning though, I'd like to keep this open so that if anybody has any comments on how it might be possible to merge these two extensions(?, I'm not sure of the terminology for these objects. There essentially partitions, right?) together, they can post.

Following on from there, I would like to mount the drive as an internal drive as it is the internal drive of the computer, rather then on /media. So I assume I can edit the fstab to mount to lets say /home2/? Or something along those lines?

EDIT: So I have actually mounted it to a folder within home which I am very happy with but its got me thinking about /hda versus /sda. Am I correct in saying that /sd's are partitions on the /hd's?

---

### Post by darkod on 2012-07-31
You can mount it as what ever you want, as long as you create that folder first. That's the great thing with the flexibility in linux.

For example, you can create a folder /mystorage if you want to:
sudo mkdir /mystorage

And then at the bottom of fstab add something like:
```
/dev/sda6   /mystorage   ext4   defaults   0   0
```

Often it's better to use the UUID string instead of /dev/sda6, like:
```
UUID=<string here>   /mystorage   ext4   defaults   0   0
```

That will make it always mount the correct partition even if you tomorrow add new disks and maybe sda becoming sdb or sdc.

But if you plan to make it /home I suggest not to touch it right now because I'm not sure if starting to use it on another mount point might create some confusion later.

As for literary joining the partitions, you can't do that. You will have to delete one and expand the other to take that space, but that also depends on the location on the disk. They have to be next to each other to be able to do that. From inside linux, it doesn't matter how many partitions there are, it works with mount points.

---

### Post by scratchesheadinvain on 2012-07-31
Thanks darko, I have mounted it to a directory within home. This suites me just fine so I am happy now although I still have some questions open to anybody just so I can understand better whats going on here.

So firstly, even though the drive has been mounted to a directory within /home, in the nautilus sidebar, it is still showing as an external drive although running ls /media shows up nothing, not even the OS partition on sda3 that has always been there.  I didn't expect the OS parttion to go missing but is this all to be expected?

> 
dbyrne@Leslie:/media$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        29G  8.7G   19G  32% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  896K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  380K  3.9G   1% /run/shm
/dev/sda6       449G   12G  415G   3% /home/dbyrne/PHD2


Maybe I'm not getting the concept of mounting. Rethinking it, I assume to mount something basically points towards a drive?

It has also got me thinking about /sda vs /hda. Am I right in saying that /sda is a partition on /hda?

Thanks again

---

### Post by oldfred on 2012-07-31
I agree with darko that it is better to use it as a separate partition, but then that is also what I ususally suggest.

I often suggest a separate /home for newer users as that makes a clean reinstall easier. But I use a separate data partition that I mount as /mnt/data and link all the data folders back into /home. Then /home looks the same but data is actually in another partition. I can easily backup /home's hidden settings and the few files that are not in my data as /home is very small. My /home is now up to 2GB but most of that is .wine with Picasa.

If you want to move /home. You already have partition, so part of it is done.
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you want to consider as data only, but link folders in:
Splitting home directory discussion and details - both links or bind:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)

The instructions on moving /home have instructions on editing fstab and setting permissions. More info or if using data partition.
Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by scratchesheadinvain on 2012-07-31
Excellent Oldfred. Thanks for the suggestions. I will have a read of these. I'm happy with having it mounted to a directory in /home so I think I will leave it this way.

---

### Post by darkod on 2012-07-31
No, sda is the first disk on the machine. Never a partition. The number means partition # on that disk, for example:
sda1 - first partition on the first disk
sdb5 - fifth partition on the second disk

hda was earlier with IDE disks. Since years ago now only sda is used in ubuntu even if you still have some old IDE disk, it will still be sda and not hda.

As for sda3, I don't know what happened. But if that's your windows system partition it best not to have it mounted all the time anyway. Once in a while windows might "get mad" if linux is touching its system partition and it can create problems from nothing.

It's best to mount it temporarily when you need it, by clicking on it. Not to have it mounted all the time.

---

### Post by scratchesheadinvain on 2012-07-31
> **darkod said:**
> No, sda is the first disk on the machine. Never a partition. The number means partition # on that disk, for example:
sda1 - first partition on the first disk
sdb5 - fifth partition on the second disk

hda was earlier with IDE disks. Since years ago now only sda is used in ubuntu even if you still have some old IDE disk, it will still be sda and not hda.

As for sda3, I don't know what happened. But if that's your windows system partition it best not to have it mounted all the time anyway. Once in a while windows might "get mad" if linux is touching its system partition and it can create problems from nothing.

It's best to mount it temporarily when you need it, by clicking on it. Not to have it mounted all the time.

Ah I see, webpage I was looking at didn't make the distinction between previous and new naming schemes. 

Also, good notice on the sda3 being windows, I completely forgot it was windows but that raises the question of why a windows partition was showing up in ubuntu?

---

### Post by oldfred on 2012-07-31
Ubuntu includes the NTFS driver so you can read & write NTFS partitions.

But it shows all the hidden files & folders that Windows tries to hide to prevent accidental damage. In Windows I used to unhide those files & folders because I wanted to see them, but too many times clicked & dragged a folder under another folder corrupting something.

Best to have a shared NTFS data partition if you want to have data from both available. Then best to automount the Windows system partition as read-only to prevent accidental damage.  If you do mount it read write just be careful and have good backups. Also do not hibernate in Windows and write into the NTFS partition that is hibernated as that will cause corruption.

---

### Post by scratchesheadinvain on 2012-07-31
Excellent thanks oldfred. While I have your attention, a few more question:

one of my earlier posts:

Even though the drive has been mounted to a directory within /home, in  the nautilus sidebar, it is still showing as an external drive although  running ls /media it doesnt show up. Is this to be expected?

Do you have any idea what could have caused this to happen in the first place?

It is my understanding that /media should only show mounted devices. Why is it showing a partition on an internal drive?

Also, just noticed that this drive which I have mounted is now NTFS. This has me worried that I've done something with the windows partition but I know that as this is sda6 then its definitely ubuntu. Why has it become NTFS?

---

### Post by oldfred on 2012-07-31
Mounts from fstab into /media or /home will appear again in the left panel in Naulitus often with an underscore and you cannot remount again as it is already mounted. Mounts to any other system partition like / (root) or /mnt will not show and to get to them you have to go to system and drill down. But that is why I use links and mount in /mnt/data. Then it only shows my links, not the mounted partition.

How did you mount it in fstab, and did you somehow reformat it?

Post these.

Mount

df -h

sudo fdisk -lu

---

### Post by scratchesheadinvain on 2012-07-31
I didn't knowingly or intentionally reformat it.

Here's my fstab (Its now called 'PHD'):

> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=e906cefb-319f-4ea7-a03d-938a800445e5 /               ext4    errors=remount-ro 0       1
UUID=a1bdd362-43d4-40a3-af01-7c2d1b04df9d /home/dbyrne/PHD               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80229593-cabe-419c-b234-c74289249a18 none            swap    sw              0       0


> dbyrne@Leslie:~$ mount
/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda6 on /home/dbyrne/PHD type ext4 (rw,errors=remount-ro)
gvfs-fuse-daemon on /home/dbyrne/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dbyrne)
/dev/sdb1 on /media/Daves type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)


dbyrne@Leslie:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda7        29G  5.3G   23G  20% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  908K  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  468K  3.9G   1% /run/shm
/dev/sda6       449G   18G  409G   5% /home/dbyrne/PHD
/dev/sdb1       3.9G  176M  3.7G   5% /media/Daves


dbyrne@Leslie:~$ sudo fdisk -lu
[sudo] password for dbyrne: 

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63      208844      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *      212992    41172991    20480000    7  HPFS/NTFS/exFAT
/dev/sda3        41172992   447696429   203261719    7  HPFS/NTFS/exFAT
/dev/sda4       447696894  1465147391   508725249    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5       508119040   523742085     7811523   82  Linux swap / Solaris
/dev/sda6       523743232  1465147391   470702080   83  Linux
/dev/sda7       447696896   508119039    30211072   83  Linux

Partition table entries are not in disk order

Disk /dev/sdb: 4105 MB, 4105175040 bytes
37 heads, 37 sectors/track, 5856 cylinders, total 8017920 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000acc9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2760     8017919     4007580    c  W95 FAT32 (LBA)


---

### Post by oldfred on 2012-07-31
I am not sure I see the issue but I see two things.

It looks like you copied the / entry for fstab. It should be more like this with defaults and 0 2 not 0 1:
See man fstab:
> The  root
              filesystem  should be specified with a fs_passno of 1, and other
              filesystems should have a fs_passno of 2.

For ext4:
UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 defaults,noatime 0 2

And you have a new 4K drive, but first partition starts at sector 63. That was what XP and older versions of Linux started at, but now everyone starts at 2048 for compatibility with the new 4K drives. The same message on your extended is not critical as you do not write into the extended but into the logicals inside the extended.

Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive.
[http://en.wikipedia.org/wiki/Cylinder-head-sector](http://en.wikipedia.org/wiki/Cylinder-head-sector)

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
it's 8-sector (4096-byte) alignment - post 8
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
Alignment issues on 4K drives
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)

---

### Post by scratchesheadinvain on 2012-08-01
OK thanks old fred, Ill have to read these posts later.

I have changed the fstab fs_passno to 2. I didn't notice any difference once I done this. 

As for the new 4k drive, I cant quite tell which your talking about but I think it maybe sdb1? If so, this is a memory key which just happened to be plugged in when I grabbed the required info. I can't see how you know it starts at sector 63 though, unless your talking about the sda drive?

Sorry if what I'm saying is confusing, I'm just a bit unsure of  how your spot the starting sector.

---

### Post by darkod on 2012-08-01
Did you also change the options for that partition in fstab? oldfred's post was not only about changing the 1 to 2, more important is to change the options to defaults because you used the same options as the root partition and those are specific for root. Notice the difference between your fstab and what oldfred posted:
```
UUID=a1bdd362-43d4-40a3-af01-7c2d1b04df9d /home/dbyrne/PHD   ext4   [COLOR=Red]errors=remount-ro   [/COLOR]0   1

UUID=076426af-cbc5-4966-8cd4-af0f5c879646 /media/Data ext4 [COLOR=Red]defaults,noatime[/COLOR] 0 2
```Of course, ignore the different UUID string and the mount point since oldfred posted one of his.

The start of a partition on sector 63 is noted in the fdisk results, look how it says sda1 partition starts at 63.

---

### Post by scratchesheadinvain on 2012-08-01
I did not change the options, I thought they where just his particular settings. Thanks darkod, I will change those. Also, I didn't see that 63 in the fdisk output, I wasn't paying enough attention.

Cool, so I assume it is recommended to change the sector start to 2048 but this would require repartitioning the drive and then a reinstall right? Apologies if this is mentioned in any of the links, I havn't read them yet.

---

### Post by oldfred on 2012-08-01
You may just be able to move the start of the partition. But that is always more risky as it has to move all data and any power failure or other stoppage corrupts everything. And Windows does not like partitions to be moved as it also has partition start & size info in its NTFS boot sector. So Windows will need chkdsk & probably fixboot repairs.

Repartition and reinstall is also a possibility or if the move does not work it may be required, so have good backups and have repair & reinstall disks, flash drives as needed.

---

### Post by scratchesheadinvain on 2012-08-01
Cool well I don't think I will attempt this, mainly from time constraints. Do you think it necessary that I do repartition? Are there foreseeable problems from leaving the start sector as 63?

---

### Post by oldfred on 2012-08-01
From what I gather it is a performance issue. Or the 4K drive will not be as efficient in writing,  as each sector is then in two drive blocks or more writing occurs.

This has some comparisons:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)

---

