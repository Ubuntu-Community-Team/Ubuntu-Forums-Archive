---
title: "Installing ubuntu on a hdd with all its Home content on it (without formating)"
date: 2018-10-16
forum: Installation &amp; Upgrades
---

### Post by Pghg022 on 2018-10-16
So i have an old, 80gb hard drive thats filled 100% (!) with a debian session installed. I have some data Home data on it that i would like to keep on the drive and i dont have an option to back it up anywhere else

Is there a way to install a fresh version of ubuntu on it without deleting the home directory with all the files and user data on it?

---

### Post by oldfred on 2018-10-16
Is your data in a separate data partition or separate /home partition?
Post this:
lsblk -f

If drive is 100%, it really is time for a new larger drive. You generally need some working room. Ubuntu hides 5%, but you should not let any system get to 100% full. 
New install will houseclean a lot but may be larger.
post this also:
df -h

---

### Post by Pghg022 on 2018-10-16
do i need to be logged in to do this? im currently on a liveboot
when ever i try to boot up the system it just crashes and i cant do anything about it

---

### Post by Pghg022 on 2018-10-16
```
NAME   FSTYPE  LABEL UUID                                 MOUNTPOINT
loop0  squashf                                            /rofs
sda                                                       
&#9500;&#9472;sda1 ext4          b1ff15b8-18e8-4f80-a5ac-60992eddc731 /media/xubuntu/b1ff15b
&#9500;&#9472;sda2                                                    
&#9492;&#9472;sda5 swap          cf09b7b4-855e-4df8-9e22-d863e725cc40 [SWAP]
sdb                                                       
&#9492;&#9472;sdb1 vfat          16C1-4DD2                            /cdrom
sr0   
```                                                    
```
xubuntu@xubuntu:~/.irssi[$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            1.9G     0  1.9G   0% /dev
tmpfs           387M  1.5M  385M   1% /run
/dev/sdb1       3.8G  1.4G  2.4G  37% /cdrom
/dev/loop0      1.3G  1.3G     0 100% /rofs
/cow            1.9G  780M  1.2G  41% /
tmpfs           1.9G   62M  1.9G   4% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.9G     0  1.9G   0% /sys/fs/cgroup
tmpfs           1.9G  524K  1.9G   1% /tmp
tmpfs           387M   84K  387M   1% /run/user/999
/dev/sda1        71G   70G     0 100% /media/xubuntu/b1ff15b8-18e8-4f80-a5ac-60992eddc731
```

---

### Post by deadflowr on 2018-10-16
It was meant that you post the output from the installed version, and not the live session.

---

### Post by oldfred on 2018-10-16
You are showing only one partition and it is at 100%.
And you have a separate swap partition.

While you say you do not have an option to backup, a 64GB flash drive is not expensive. And your data would probably fit into it, as system is using multiple GB itself.
If your data is at all valuable you need to have a backup.

Any install option that might keep your data in /home has a risk of overwriting it. Just a difference in a check box on formatting will either erase all data or overwrite just system data.
       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

