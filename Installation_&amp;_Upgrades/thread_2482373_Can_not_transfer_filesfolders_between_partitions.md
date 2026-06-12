---
title: "Can not transfer files/folders between partitions"
date: 2022-12-29
forum: Installation &amp; Upgrades
---

### Post by n-m-talati on 2022-12-29
Friends,

Ubuntu Studio is very new to me. I seek your guidance to resolve my issue, I am facing.

My system is: 
MoBo.---> Asus ROG Strix B550-F Gaming with Wi-Fi II
Processor---> Ryzen 5 5600G
RAM ---> 32 GB DDR4
O.S.---> Windows 10 + Ubuntu Studio 22.04 LTS ----> on TWO separate hard discs.

NVMe. 250 GB internal hard disk installed with Win-10
SSD 250 GB installed recently "Ubuntu Studio 22.04 LTS"

Also have other 4 HHDs for Data ( 1 TB + 1 TB + 250 GB + 250 BG)

My question/difficulty is that, I am unable to transfer any of my file or folder from "US 22.04" to any of above partitions or vise-versa. (cut/copy and paste)
From Win-10, I can not transfer files/folders to US-22.04 (cut/copy and paste)

Please help me in resolving this issue.
Regards to all in anticipation.

---

### Post by TheFu on 2022-12-29
So, Linux uses different file systems than Windows. These are generally incompatible.  There are file system drivers that can "mount" a foreign file system, but the limitations of the file system don't allow those to be locally accessed without some knowledge.

In Unix systems, file and directory permissions matter.  They are the core of security.  So, to access the NTFS or exFAT or FAT32 storage that MS-Windows uses requires not only the correct drivers, but the correct mount options to allow your userid to have the desired access to that/those file systems.  This can be dangerous, but things usually work.

Going from Windows into Linux file systems has always been harder and always seemed like a terrible idea to me.  I've heard of 3rd party, commercial, drivers to make this possible, but I've never used them.

Since I don't dual boot, when I need to transfer files between 2 computers, I'll use sftp or scp or rsync solutions.  These are extremely standard in the Unix world and have been since the mid-1990s. They all use ssh at the core and are considered secure enough to use over the internet, assuming ssh-keys are used for authentication, not passwords.

On the same LAN, people usually will connect to an Ubuntu system running Samba, which is the CIFS network protocol that MS-Windows uses.

Step 1: Learn about Unix file and directory permissions. Learn this sooner than later.  Every file (directories are just special files), as an owner, group, permissions and optional ACLs and xattrs.  Google "Ubuntu file permissions", but **any** Unix book in the last 40+ yrs should have a chapter about this.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is one, free, no-hassle, book.  It is available in a few different languages.

Step 2: Under stand that Unix systems expect an admin to "mount" storage, create file systems, and open the permissions for specific groups of users.  The /etc/fstab is the typical method used to mount internal or always connected storage.  "ubuntu fstab ntfs" would be a good search term.  For NTFS, [Https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822](Https://ubuntuforums.org/showthread.php?t=2420861&p=13865822#post13865822) might be what you seek.

If you are in a hurry, try:
```
  # Non-native file systems - ntfs, exfat, fat32
  sudo mkdir /media/canon  # the mount point (i.e. empty directory must pre-exist
  sudo mount -t auto -o uid=$USER /dev/sdb1 /media/canon
```

where
 - /dev/sdb1 is the device filename for the file system/partition.  This can change with every boot, so it is suggested to use UUID= or LABEL= options.  The 'blkid' command will show the device filename, UUID and any LABEL.  Most partitioning tools allow adding a LABEL, which is good for normal humans.  Don't mount an already mounted device file. That would be bad, probably.  Always check that you have the correct device filename.  If your MS-Windows install is on an NVMe SSD, the device partition name will probably start with nvme..... something.  Don't try to mount the entire storage device. If you don't know which is which, STOP!  It would be terrible to wipe your install, right?

 - /media/canon is the empty directory where the file system will be mounted with the options provided. It must exist BEFORE the mount will work. It can be anywhere, but you probably want to only place it under either /mnt/ or /media/ until you understand the possible problems in putting mounts other places.

The mount command above isn't optimal, but it should work for the main user, assuming he has sudo.
A handy command (I'd use an alias if I were you):
```
$ lsblk -e 7 -o name,size,type,fstype,mountpoint,label,uuid
```

Clear as mud?

You'll see chown and chmod and chgrp commands in the tutorials.  Those commands will never, ever, ever, work on foreign file systems like NTFS or exFAT.

---

### Post by TheFu on 2022-12-29
Microsoft has been lying to you for decades, when they call things a "drive letter", that's a complete lie.  A drive letter maps to a partition on Windows.  Linux, in a simple storage setup, will place a file system onto a partition (the admin will do this), and mount the partition.

Earlier this month, I did a long post explaining partitions, disks, numbers, letters, to clarify for someone else.  Hopefully, you can find that post or some other explanation elsewhere to make it clearer.  

Linux also supports enterprise storage management that don't use partitions in the simplistic way I've assumed.  If you happen to be using LVM2 or ZFS or BTRFS, then things are different and the steps are different.  Some variations of NTFS also support more complex storage management, but if "Basic Partitions" are used as seen inside Windows, then it shouldn't be hard.

Also, MSFT doesn't fully close file systems when you think you are shutting down the computer. They do this to trick the computer into starting faster, but no Linux OS will touch a file system marked as "open", so there are 2-3 settings which have to be toggled from inside MS-Windows before Linux will allow mounting NTFS.  Sorry, I don't recall the exact names of those things, but "fast boot" or "hibernation" are what my brain is saying now.  Hopefully, someone else will cover that shortly in their posts OR you can find it in these forums.  The question isn't exactly unique. ;)

---

### Post by oldfred on 2022-12-30
Windows uses fast start up which sets the hibernation flag.
The Linux NTFS driver will not default mount hibernated Windows partitions. You can force mount as read only using command line.

Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/](https://www.elevenforum.com/t/turn-on-or-off-fast-startup-in-windows-11.1212/)

---

