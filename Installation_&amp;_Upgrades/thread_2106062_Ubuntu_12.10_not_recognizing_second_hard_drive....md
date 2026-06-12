---
title: "Ubuntu 12.10 not recognizing second hard drive..."
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by HippieDave on 2013-01-17
Just installed 12.10 on a brand new desktop.  I'm running a 250 GB SSD as my main drive, and I also installed a 1TB second drive  which I hope to use to hold a backup of the main drive, as well as the primary repository for all my music and photography files.  I had an old 160 GB drive installed as well, on which resides an old windows OS for the rare instances in which I find a need for windows. Finally, I have a 750GB external drive for additional backup.

During install, all three internal drives were 'seen'. After install, however, only the SSD and the old windows drive are recognized. as internal drives.,  The external drive mounts fine too.  But the 1TB secondary internal drive  doesn't show up anywhere.  What can I do?

---

### Post by papibe on 2013-01-17
Hi HippieDave.

Could you post the results of these commands?
```
mount -l

sudo fdisk -l
```
Regards.

---

### Post by HippieDave on 2013-01-18
Here is the response to mount -l 


/dev/mapper/ubuntu-root on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
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
/dev/sda2 on /boot type ext2 (rw)
/dev/sda1 on /boot/efi type vfat (rw)
gvfsd-fuse on /run/user/david/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=david)
/dev/sdh1 on /media/david/WD Back-up type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [WD Back-up]
/dev/sdc1 on /media/david/9E405D3C405D1C79 type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096)


And I got this to sudo fdisk -l

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1   488397167   244198583+  ee  GPT

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab18bbd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   312576704   156288321    7  HPFS/NTFS/exFAT

Disk /dev/mapper/ubuntu-root: 241.3 GB, 241331863552 bytes
255 heads, 63 sectors/track, 29340 cylinders, total 471351296 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu-swap_1: 8266 MB, 8266973184 bytes
255 heads, 63 sectors/track, 1005 cylinders, total 16146432 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu-swap_1 doesn't contain a valid partition table

Disk /dev/sdh: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x44fdfe06

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1            2048  1465145343   732571648    7  HPFS/NTFS/exFAT


I am still finding my way around the new desktop look for 12.10 (I'm used to 10.04.  But I found "computer"  and it lists all drives.  When I try to open the 1 TB drive, I get a 'cannot mount drive' message. Thank you for helping!

---

### Post by papibe on 2013-01-18
It looks like missing drive is /dev/sdb

Does it appear on nautilus when you go to?
```
Go -> Computer
```

If not, could you post an screenshot of gparted?

Regards.

---

### Post by HippieDave on 2013-01-18
Thanks Papibe:

The drive is there in "computer".  If I try  to open it I get a 'cannot mount' message.

btw, when I try to run 'gparted' I get an message that root privileges are needed and I don't have them.  How is this possible, as I am originator/only user of system?

---

### Post by oldfred on 2013-01-18
You should be able to use gparted on other drives, but not on your current drive. But it should show your current drive. When you start gparted it should ask for your password.
You can also try from command line:
gksudo gparted

Is your 1TB drive new and not partitioned yet, or is it damaged?

> Disk /dev/sdb doesn't contain a valid partition table

---

### Post by HippieDave on 2013-01-18
The whole computer --including the 1TB drive--is new.  I just used the install wizard to install on the SSD --I didn't manually partition anything, as i am not feeling real solid about that.  So that is probably the answer.  1) Is there a way to address this drive --i.e., partition it if that is what is necessary--without reinstalling the OS? and 2) if I do have to manually partition it, how the heck do I do that.  Sorry for such a simple Q, but while I'm a long time Ubuntu user, I really am a newbie when it comes to getting in under the covers.

---

### Post by HippieDave on 2013-01-18
Taking hints from all your questions, I found these instructions on how to ADD a new drive --

[https://help.ubuntu.com/community/InstallingANewHardDrive--](https://help.ubuntu.com/community/InstallingANewHardDrive--)

these walked me through partitioning it and the computer now mounts it automatically upon boot.  All LOOKS well...now I just have to figure out how to tell applications to save music, photos, docs etc to files on that drive! Thank you all.  Any additional hints or links to sources on how I should manage this drive are welcome.

---

### Post by ronparent on 2013-01-18
/dev/sdb appears as a broken raid - which apparently you don't want to use it as such! The long term solution is to permanently erase the raid meta data from sdb - ie
> sudo dmraid -Ea /dev/sdb

for good measure also uninstall dmraid. ie
> sudo apt-get purge dmraid

You should then be able to use sdb as you please!

---

### Post by oldfred on 2013-01-18
If you mount your data partition(s) with fstab then you can link them into /home as either replacements for current folders like Music or as other folder with a different name. I use linking folders from one mount of a data partition in fstab, some others prefer using bind which adds each folder in fstab.  Supposely some advantages of bind if using networking & sharing. I only use one PC so linking has worked for me.

       I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root).
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
Link is on move home but see post by bodhi.zazen on data partition #6
[http://ubuntuforums.org/showthread.php?t=325048](http://ubuntuforums.org/showthread.php?t=325048)

    
       Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

---

### Post by HippieDave on 2013-01-18
Thanks for the assistance, although I honestly don't follow the last couple of suggestions:)  I have the drive mounting now, but it is 'owned' by root, and will not let me open files etc on it.  I don't understand how I do not have root permission in this circumstance (brand new install on new PC)...how do I get root authority?

---

### Post by oldfred on 2013-01-18
You do not use root, but you change to your ownership & permissions.

If you mount it in fstab then you can have it mounted all the time.

Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
       [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
     
    If you have it mounted unmount it. This is a manual mount to let you set ownership & permissions but fstab is better. Change sda5 to your sdbX or whatever your second drive's partition is.

       sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
chmod -R a+rwX,o-w /mnt/data
sudo chown $USER:$USER /mnt/data
#if not known to list partitions
sudo fdisk -l

       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6

---

### Post by HippieDave on 2013-01-19
When I try 'sudo mkdir /mnt/data' its says it cannot as dir already exists.

When I try the other commands you suggest I get a="operation not permitted " or "permission denied" message

---

### Post by oldfred on 2013-01-19
You can only make the mount point once, unless you remove it.

If partition is already mounted it will not let you mount it again. Unmount it.

Are you copying commands. Sometimes spaces are not as obvious depending on fonts.

---

### Post by HippieDave on 2013-01-20
I unmounted it using the 'unmount'option when you right click;

then I copied and pasted the suggested commands.

---

### Post by fonsi2099 on 2013-05-16
> **ronparent said:**
> /dev/sdb appears as a broken raid - which apparently you don't want to use it as such! The long term solution is to permanently erase the raid meta data from sdb - ie


for good measure also uninstall dmraid. ie


You should then be able to use sdb as you please!

I get this answer:
sudo dmraid -Ea /dev/sdb
ERROR: invalid option argument for -a

What I need to update?

Many thanks

---

### Post by oldfred on 2013-05-16
I do not know all the switch settings. 
But this is what I have seen before.

 sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

---

