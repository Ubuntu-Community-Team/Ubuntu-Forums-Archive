---
title: "Upgrading 12.04 to 14.04 on DELL Vostro 3500 -- more problems"
date: 2014-07-22
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2014-07-22
Here is what the upgrade did on file structure:

It took /media/FolderA and /media/FolderB and then made /media/myname/FolderA and /media/myname/FolderB and then deleted the contents from /media/FolderA and /media/FolderB.  Those later two foldera are partitions on the SSD.

Each of those folders have numerous subfolders and each of those folders have about 30 GB each of data.

i hope there is a rational explanation for what happened.

John

---

### Post by yancek on 2014-07-22
Are you saying that the files/directories under /media/myname/FolderA and FolderB are gone also? 

> i hope there is a rational explanation for what happened.

I have no idea why this was done but I'm sure there is an explanation somewhere, whether rational or not is probably a matter of opinion.  The link below has a little info on it.

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

### Post by cigtoxdoc on 2014-07-23
Here is what upgrade to 14.04 did to file structure on SSD.  It took /media/MyChemistry and made it /media/john/MyChemstry.  The change also shows on gparted.

John


NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 223.6G  0 disk 
&#9500;&#9472;sda1   8:1    0 126.6G  0 part /media/OS
&#9500;&#9472;sda2   8:2    0     1K  0 part 
&#9500;&#9472;sda3   8:3    0  19.5G  0 part /media/john/MyChemistry
&#9500;&#9472;sda5   8:5    0  32.5G  0 part /media/john/MyDocuments
&#9500;&#9472;sda6   8:6    0    41G  0 part /
&#9492;&#9472;sda7   8:7    0   3.9G  0 part [SWAP]
sr0     11:0    1  1024M  0 rom

---

### Post by bapoumba on 2014-07-23
When installing, did you select these partitions, choose a mount point and untick the format box (ie say not to format) ? Did you have a separate /home, if so, did you use it as the new install /home ?
Please post the outputs to :
```
cat /etc/fstab
mount
```

---

### Post by cigtoxdoc on 2014-07-23
The original partitions were set by editing /etc/fstab using instructions I received on this forum.  I have several other PCs setup the same way.  On the upgrade, I took the "upgrade" option that was not suppose to mess with anything but the partition containing Ubuntu.  See [http://ubuntuforums.org/showthread.php?t=2204340&highlight=fstab](http://ubuntuforums.org/showthread.php?t=2204340&highlight=fstab).  

john@john-Vostro-3500:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

#Entry for /dev/sda6 :
UUID=186a60b4-1970-4676-8fa8-b3ab698fcfe1       /       ext4    errors=remount-ro       0       1
#Entry for /dev/sda1 :
UUID=06550BF50F315FAE   /media/OS       ntfs-3g defaults,locale=en_US.UTF-8     0       0
#Entry for /dev/sda7 :
UUID=7bef8b10-bd81-443f-9e54-4344aed9a799       none    swap    sw      0       0


john@john-Vostro-3500:~$ sudo mount
[sudo] password for john: 
/dev/sda6 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/cgroup type tmpfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
none on /run/user type tmpfs (rw,noexec,nosuid,nodev,size=104857600,mode=0755)
none on /sys/fs/pstore type pstore (rw)
/dev/sda1 on /media/OS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
systemd on /sys/fs/cgroup/systemd type cgroup (rw,noexec,nosuid,nodev,none,name=systemd)
gvfsd-fuse on /run/user/1000/gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev,user=john)
/dev/sda5 on /media/john/MyDocuments type ext4 (rw,nosuid,nodev,uhelper=udisks2)
gvfsd-fuse on /root/.gvfs type fuse.gvfsd-fuse (rw,nosuid,nodev)
/dev/sda3 on /media/john/MyChemistry type ext4 (rw,nosuid,nodev,uhelper=udisks2)

How do I change /media/john/MyDocuments into /media/MyDocuments?

John

---

### Post by bapoumba on 2014-07-23
These two partitions are not in your fstab as they were before. When you mount them from the file browser, they end up in /media/<your_user>/
Any reason why you have not mounted them in fstab ?

---

### Post by oldfred on 2014-07-23
I think you were just using default mounts via Nautilus not fstab.

And with 12.04 the default mount was in /media. But in later versions and 14.04 it was changed to /media/$USER where $USER is your log in name. 
Some complaints on why, but it seems to be for security that only the user should mount it.

---

### Post by cigtoxdoc on 2014-07-23
Thank you for your replies.  Again, as I stated earlier, the partition s were mounted by editing fstab as per [http://ubuntuforums.org/showthread.php?t=2204340&highlight=fstab](http://ubuntuforums.org/showthread.php?t=2204340&highlight=fstab).  I have several other PCs setup the same way.  On the upgrade, I took the "upgrade" option that was not suppose to mess with anything but the partition containing Ubuntu.

I have not yet put them back with fstab as I obviously would have made a mistake by not doing it with /media/$USER.

John

---

