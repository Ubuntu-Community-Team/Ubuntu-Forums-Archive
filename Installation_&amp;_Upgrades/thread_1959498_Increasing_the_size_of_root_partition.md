---
title: "Increasing the size of root partition"
date: 2012-04-15
forum: Installation &amp; Upgrades
---

### Post by ylk on 2012-04-15
I am interested in increasing the size of the root (/) partition.
Here's some disk usage info ...

adam@ASUS-LAPTOP:~$ df -H
Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1              9.9G   7.6G   1.9G  81% /
none                   4.2G   336k   4.2G   1% /dev
none                   4.2G   2.3M   4.2G   1% /dev/shm
none                   4.2G   287k   4.2G   1% /var/run
none                   4.2G      0   4.2G   0% /var/lock
none                   4.2G      0   4.2G   0% /lib/init/rw
/dev/sda6              475G    69G   383G  16% /home
 adam@ASUS-LAPTOP:~$
adam@ASUS-LAPTOP:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=6f40ecfb-c0eb-4c2d-a9a6-6a6672db35a2 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=2a875a2a-8088-4844-be48-337a2ee3200d /home           ext3    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=73889cf0-db54-453c-92cf-384014a018cb none            swap    sw              0       0
adam@ASUS-LAPTOP:~$

Any suggestions?

---

### Post by oldfred on 2012-04-16
Moved to new thread as old thread was old and that poster had a different partition layout, so info in it did not apply.

The df -H does not show where the partitions are on the drive. You cannot easily move space from one end to another. 

It would help to post a screenshot from gparted.

---

### Post by ylk on 2012-04-16
Thanks, here's the requested screenshot of GParted ...

[http://imageshack.us/photo/my-images/32/screenshotdevsdagpartedb.png/](http://imageshack.us/photo/my-images/32/screenshotdevsdagpartedb.png/)

---

### Post by oldfred on 2012-04-16
I see two choices. 

What you want directly is to shrink /home, then move /home right, then move the extended's start right, and then expand / into the unallocated. I would do each as a separate step and make sure everything works after each step.

That is a lot of moving. Moving data can take a very long time and any interruption, power failure, user stopping system change, etc fully corrupts system, so be sure to have good backups.

Another choice is just to shrink /home by 25GB, and create a new partition for a new /. Then you can install a clean new system with out a lot of moving of data. You could still boot old root. You can export list of installed applications if a lot and reinstall so you have everything the way it was.

If you save a screenshot you can upload it by using the paperclip icon in the edit panel above your message.

---

### Post by ylk on 2012-04-16
Thanks, with the upcoming LTS release of Ubuntu,
I prefer the 2nd root (/) partition approach.  Excellent suggestion!

Hopefully, I will not lose data when decreasing the size of /home partition,
since my VirtualBox guest OSes are there.

BTW, I like the paperclip/Attachments suggestion.  Thanks!
Too bad it's not available when editing posts previously sent.


For self-reference ...

[http://www.psychocats.net/ubuntu/backup](http://www.psychocats.net/ubuntu/backup)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

[https://help.ubuntu.com/community/LinuxFilesystemsExplained](https://help.ubuntu.com/community/LinuxFilesystemsExplained)
=========================================================
_**Fragmentation**_

Another  common Windows practice that is not needed in Unix is defragmenting the  hard drive.  When NTFS and FAT write files to the hard drive, they don't  always keep pieces (known as blocks) of files together.  Therefore, to  maintain the performance of the computer, the hard drive needs to be  "defragged" every once in a while.  This is unnecessary on Unix File  systems due to the way it was designed. When ext3 was developed, it was  coded so that it would keep blocks of files together or at least near  each other. 

No  true defragmenting tools exist for the ext3 file system, but tools for  defragmenting will be included with the ext4 file system. 
=========================================================

---

