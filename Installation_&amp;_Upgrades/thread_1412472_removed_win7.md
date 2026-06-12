---
title: "removed win7"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by chris.olive on 2010-02-21
I have removed the trial of win 7 and want to use the empty space for Ubuntu 9.10, [46gb]. 
Opening disk utility shows 60gb hard drive, divided into system reserved 105mb, 46gb file system [Linux ext4 [version 1]], 13gb extended [contains no logical partitions], 13 gb [Linux ext4 [version 1]], 617mb swap space.
Because I have given the 46gb space the same name as the 13gp space i.e. [Linux ext4 [version 1]],will this now be used By Ubuntu for data storage or do I need to do a complete re-install?
Any comments/ advice welcome.

---

### Post by donaldmartin on 2010-02-21
For data storage - do you mean to store files and whatnot on it, or for SWAP space?

---

### Post by oldfred on 2010-02-21
You do not need to reinstall, just create a mount point, give it permissions and mount it. If you want to permanently mount it you can add the mount to fstab. You can mount it anywhere and use it or mount it somewhat hidden and use links to see the data folders in /home.

Share data partition
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
see ridgeland's post in ubuntu forums
[http://ubuntuforums.org/showthread.php?t=1197773](http://ubuntuforums.org/showthread.php?t=1197773)

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

NOTE: The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not.

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition for the Data

if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.
$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /Data
where fred should be your login name

But it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager

---

### Post by chris.olive on 2010-02-23
Sorry storage only, i.e. free space
Chris

---

### Post by chris.olive on 2010-02-23
Oldfred
I think it must be already sorted, when I open disk utilty there are two [as stated] Linux ext 4 [version 1] filesystems shwn.
Took your advice and loaded storage device manager this shows four partions only where as disk utilty shows  [system reserved 105mb, 46gb file system [Linux ext4 [version 1]], 13gb extended [contains no logical partitions], 13 gb [Linux ext4 [version 1]], 617mb swap space.] shows five two of which have the same name so I take this to mean that both ext 4 are treated the same and just shown split?

---

### Post by oldfred on 2010-02-23
If it is two partitions they are not the same but split unless you are running some special software that combines them. You just have to mount the data partition to be able to use it.

---

### Post by chris.olive on 2010-02-25
Many thanks to you all it solved itself, the whole screen was black yesterday morning and needed a reinstall.

---

