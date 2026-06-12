---
title: "Adding a HD"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by 9a8sy on 2010-02-14
I just installed 9,10 on my desktop which has 2 Hard Drives, an IDE and a SCSI. I let Ubuntu do the partitioning but I'm having trouble accessing the second drive which is the SCSI. When I try to go to it, it has a pop up window that says "Authentication is required to mount this device". I can enter my password and then I see the lost+found folder on it. My question is how to I make this drive available without going through the authentication process everytime? I'll attach additional info below:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda1            111115968   2761816 102709716   3% /
udev                    739616       292    739324   1% /dev
none                    739616      1212    738404   1% /dev/shm
none                    739616        84    739532   1% /var/run
none                    739616         0    739616   0% /var/lock
none                    739616         0    739616   0% /lib/init/rw
none                 111115968   2761816 102709716   3% /var/lib/ureadahead/debugfs
dennis@Ubuntu-desktop:~$ cat  /proc/partitions
major minor  #blocks  name

   8        0  117220824 sda
   8        1  112888723 sda1
   8        2          1 sda2
   8        5    4329486 sda5
   8       16   35548320 sdb
   8       17   35543781 sdb1

---

### Post by darkod on 2010-02-14
Is this second hdd ntfs partition or linux partition?
For ntfs you can install ntfs-config with:
sudo apt-get install ntfs-config

After it installs it will be in System-Administration. With the second disk UNMOUNTED open that tool and it will detect it, and it will also ask you if you want to automount at every boot.
This is the easiest way, you can also edit manual fstab but that is more risky if you aren't used to it.

If that disk is linux partition, I think you have to edit manually fstab but reseach more about it. Making wrong edit in fstab can block you booting your ubuntu.

---

### Post by oldfred on 2010-02-14
The default does not automatically give permissions or ownership. You should understand mounting and if you want to permanently mount it understand fstab.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

You still should understand fstab and mount as some of the settings may be important but:
But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by 9a8sy on 2010-02-14
This machine originally had XP on it so maybe that second drive has ntfs on it still. I would think it would be better to make it a linux partition unless I was making this a dual boot or something wouldn't I?

---

