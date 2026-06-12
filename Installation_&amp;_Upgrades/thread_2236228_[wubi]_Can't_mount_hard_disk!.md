---
title: "[wubi] Can't mount hard disk!"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by Haris_LinuxOS on 2014-07-25
I have updated ubuntu 10.04 to 12.04.
Now I can't mount the disk
It says "a hard disk check failed"
Also when I try to delete a file, it says "rm: filesystem is readonly" etc
The file system isn't readonly. 
I was able to write a file from my windows 7.
I am sure that the problem was happened from the update.
i don't want to lose my files.
(note: i have installed wubi not in the windows partition, i have installed it on another one)

---

### Post by vanadium on 2014-07-25
Try to be more clear in expressing the issue. you are working from within 12.04? What disk it is you cannot mount? What do you attempt to perform the mounting? What do you mean with "write a file from my windows 7"?

---

### Post by Haris_LinuxOS on 2014-07-25
I was using Ubuntu 10.04 and all were OK. I have decided to upgrade it to 12.04.
The upgrade process run smootly, but after reboot, i can't boot to ubuntu.
I have tried selecting all kernel versions and recovery mode, but nope.
When I start ubuntu, it says "hard disk check failed. press control+d to ignore and continue booting, a maintance shell will run right now"
Startx doesn't work "configuring displaye failed"
And when I try to delete a file, I type, *for example* rm /home/linuxos/file and then it says rm: the filesystem is read-only.
Also when I try to install a program with apt-get, it says the same

---

### Post by Haris_LinuxOS on 2014-07-25
With "write a file from my windows 7" i mean that I am able to write a file to the partition I have wubi installed.
Please note that i **haven't **installed wubi on the C;/ drive.
I have installed it to another partition.

---

### Post by vanadium on 2014-07-25
> 
    When I start ubuntu, it says "hard disk check failed. press control+d to ignore and continue booting, a maintance shell will run right now"
    Startx doesn't work "configuring displaye failed"

Are you able to drop to a maintenance shell? If you can, then have the file system checked with the "fsck" command. For this, you would need to know the device name of the partition ("sudo blkid" or "sudo fdisk -l"). The drive must *not* be mounted ("sudo umount ...").

I am afraid, though, that this may not help getting to a properly booting system, even if you are sufficiently technically savvy to complete these steps successfully. In any case, if you have personal data on the volume, copy it out to a safe location. If after checking the disk the system still does not start, then you probably will need to reinstall (fresh - although upgrading is officially supported, it does not always work smoothly). While you are at it, you might as well create a dedicated partition for your Ubuntu installation. Technically superior and more safe.

---

### Post by hakuna_matata on 2014-07-26
My suggestion:

[LIST]
[*]First of all, run **chkdsk** to check your Windows file system: Go to *Computer* on Windows 7, right  click the drive (e.g. D: ) you installed Ubuntu on, select  Properties, select the Tools tab, then under *Error-checking* click *Check now. *Select *Automatically fix file system errors*. 
[*]Start Ubuntu in *Recovery Mode*, select *Root Shell, *check your Linux file system on virtual partition: ```
fsck -f /host/ubuntu/disks/root.disk
``` 
[*]If your file system is clean, try to remount your virtual partition: ```
mount -o remount,rw /dev/loop0
``` 
[*]If that also works, try to reboot from root shell.```
exit
``` and select *Resume* 
[/LIST]

If it is 14.04 and not 12.04:
```
lsb_release -d
```
try [http://ubuntuforums.org/showthread.php?t=2217829](http://ubuntuforums.org/showthread.php?t=2217829)

---

### Post by Haris_LinuxOS on 2014-07-26
Solved by installing ubuntu normaly (from cd, not from wubi)
thanks for your repplies.

---

