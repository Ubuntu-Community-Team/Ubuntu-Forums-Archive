---
title: "Cant find files"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by stuwoody007 on 2011-01-07
hello all - am new to linux and have had a system crash - cannot figure out what is wrong and need to recover my files.

Where are my files kept and does ubuntu have a recovery programe

HHHEEEELELLLLLLPPPPPPPP!!!!!!\

thanks stu

---

### Post by stuwoody007 on 2011-01-07
Error messages coming up

Unable to mount 990 GB Filesystem

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending

---

### Post by presence1960 on 2011-01-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

### Post by stuwoody007 on 2011-01-07
Thanks but will not finish came up with

Unable to mount 990 GB Filesystem

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.  Possible causes include: the remote application did not send a reply,  the message bus security policy blocked the reply, the reply timeout  expired, or the network connection was broken.

stuck on terminal 

Identifying MBRs...
Computing Partition Table of /dev/sda...
Computing Partition Table of /dev/sdb...
Searching sda1 for information... 

dont think its going any further

---

### Post by presence1960 on 2011-01-07
From the desktop of Live CD open a terminal and run ```
sudo e2fsck /dev/sdX -y -f -v -c
``` where X in sdX = the 990 GB disk designation, such as sda, sdb, etc.

You may have filesystem errors preventing mounting and reading of the disk. Hopefully this will fix those errors.

---

### Post by stuwoody007 on 2011-01-07
thanks for your help - new to linux - here are the results: does not look good - assumed X is a or b as only 1 hdd installed

ubuntu@ubuntu:~$ sudo e2fsck /dev/sdb -y -f -v -c
e2fsck 1.41.12 (17-May-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda -y -f -v -c
e2fsck 1.41.12 (17-May-2010)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?
ubuntu@ubuntu:~$

---

