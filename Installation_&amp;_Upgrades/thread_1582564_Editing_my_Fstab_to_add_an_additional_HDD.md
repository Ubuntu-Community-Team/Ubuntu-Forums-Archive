---
title: "Editing my Fstab to add an additional HDD"
date: 2010-09-26
forum: Installation &amp; Upgrades
---

### Post by Drdog on 2010-09-26
Let me start by saying that I am new to Linux. I'm attempting to add an additional HDD to my system (without having to format it). I was told that I need to edit my Fstab.

I'm trying to get an internal SATA drive mounted.

I'm getting these two errors when I try and mount the drive

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


and 


DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending


my Fstab is as follows.


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=84ec7664-2d32-4b7c-8ec4-36bc0570adbb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6be3be1d-78a2-404b-a41f-34131b81ce69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


If there is anything I could do to get this drive to mount or maybe clean up my Fstab a bit please let me know!

---

### Post by sikander3786 on 2010-09-26
Which File System on your additional HDD? You want to make it accessible in Windows (if dual booting) or only use it in Ubuntu?

---

### Post by Drdog on 2010-09-26
I just want an extra HDD on my system, I don't have windows installed at all. I just want to be able to access the files on this second HDD.

---

### Post by perspectoff on 2010-09-26
You have to have a partition on your second hard drive, first. Use GParted to see what partitions are there, if any. If not, you will have to create one.

You can also see your partitions (and their UUIDs):
 sudo blkid

The first hard drive (if SCSI) will have partitions:

/dev/sda1
/dev/sda2

etc.

and the second hard drive

/dev/sdb1
/dev/sdb2

etc.


fstab references partitions.

But you said you didn't want to format the second hdd. What is on it now?

---

### Post by Drdog on 2010-09-26
I actually have linux on the other HDD too. 

In gparted it's saying I have 

"/dev/sda1 *then a key symbol File System:ext4 Mountpoint: /

and

/dev/sda2 FileSystem:Extended and nothing for mount point
     /dev/sda5 Filesystem:Linux-swap and nothing for mount point."


blkid turned up this

/dev/sda1: UUID="84ec7664-2d32-4b7c-8ec4-36bc0570adbb" TYPE="ext4" 
/dev/sda5: UUID="6be3be1d-78a2-404b-a41f-34131b81ce69" TYPE="swap" 
/dev/sdb1: UUID="712848ed-766a-4762-bf81-cda65954b115" TYPE="ext4" 
/dev/sdb5: UUID="a6f0c700-1571-479d-a719-f7f99bca370a" TYPE="swap"

---

### Post by sikander3786 on 2010-09-26
Follow post # 2 in the following thread.

[http://ubuntuforums.org/showthread.php?t=1482818](http://ubuntuforums.org/showthread.php?t=1482818)

---

### Post by Drdog on 2010-09-26
my UUID for the drive I'm trying to mount is "712848ed-766a-4762-bf81-cda65954b115" TYPE="ext4" I'm not sure how to edit my Fstab, I have it opened but it won't let me change anything in it. I think I need to open it with sudo permission? I'm not sure how to do that.

---

### Post by sikander3786 on 2010-09-26
```

gksu gedit /etc/fstab

```

---

### Post by Drdog on 2010-09-26
when I try to save my fstab file it says "Could not find the file /ect/fstab."

---

### Post by sikander3786 on 2010-09-26
It is not "ect" it is "etc".

---

### Post by Drdog on 2010-09-26
ok I edited my Fstab and restarted and got this when I tried to open the drive


Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sdb1 on /media/Data




this is my Fstab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=84ec7664-2d32-4b7c-8ec4-36bc0570adbb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6be3be1d-78a2-404b-a41f-34131b81ce69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
UUID=712848ed-766a-4762-bf81-cda65954b115 /media/Data ext4 defaults 0 0

---

### Post by sikander3786 on 2010-09-26
It might be happening because root is the owner of /media/Data.

```
sudo umount /media/Data
```

```
sudo chown root:user /media/Data
```

Replace user with your username.

```
sudo chmod 770 /media/Data
```

And finally without **sudo** this time,

```
mount /media/Data
```

Reboot after completion and see if the drive gets mounted this time.

[COLOR="Red"]**EDIT:**[/COLOR] Replace user with your username as edited above.

---

### Post by Drdog on 2010-09-26
I followed your instructions and this is exactly what happen


nawt@nawt-desktop:~$ sudo umount /media/Data
[sudo] password for nawt: 
Sorry, try again.
[sudo] password for nawt: 
umount: /media/Data: not mounted
nawt@nawt-desktop:~$ sudo chown root:nawt /media/Data
nawt@nawt-desktop:~$ sudo chmod 770 /media/Data
nawt@nawt-desktop:~$ mount /media/Data
mount: only root can mount /dev/sdb1 on /media/Data

---

### Post by sikander3786 on 2010-09-26
My last shot. Try changing defaults to user, it should surely let mount the drive regardless of root account.

```
UUID=712848ed-766a-4762-bf81-cda65954b115 /media/Data ext4 **defaults** 0 0
```

To

```
UUID=712848ed-766a-4762-bf81-cda65954b115 /media/Data ext4 [COLOR="Magenta"]user[/COLOR] 0 0
```

---

### Post by Drdog on 2010-09-26
That didn't work either....and for some reason now I have a filesystem in computer named "Data" and I have no clue what it is or how it got there..


The problem with mounting happens before I even log into Ubuntu.....

At the login screen it says "Error to mount drive /media/Data"

Press S to skip mounting or M for something?

---

### Post by Drdog on 2010-09-26
Now I'm getting 

"A job is pending on /dev/sdb1"


This is my "fstab". The bottom line being the drive I'm trying to mount.

I've been at this for a good 6+ hours with no avail.

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=84ec7664-2d32-4b7c-8ec4-36bc0570adbb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=6be3be1d-78a2-404b-a41f-34131b81ce69 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1    /media/mynewdrive   ext3    defaults     0        2



Sudo fdisk -l displays this



Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18657   149862321   83  Linux
/dev/sda2           18658       19452     6385837+   5  Extended
/dev/sda5           18658       19452     6385806   82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc4167ab8

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29952   240589408+  83  Linux
/dev/sdb2           29953       30515     4522297+   5  Extended
/dev/sdb5           29953       30515     4522266   82  Linux swap / Solaris



If there is anymore information I can post to help me resolve this issue please just let me know the command and I will make sure to post it. Thanks!

---

