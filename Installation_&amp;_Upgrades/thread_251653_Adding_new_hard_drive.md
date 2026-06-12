---
title: "Adding new hard drive"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by tr0910 on 2006-09-05
I installed 6.06 onto an old Athlon machine and nuked an old 80 gig drive to do it.  Installation was a breeze, so I unplugged the CDrom used for installation and plugged in another old ATA HD to where the CD was attached (hoping I could just plug and play).  Now I have a conflict with HDC. 

fstab still reporting it as a CDROM and in fdisk reporting it correctly.  File browser mounts this second drive in /tmp somewhere and when I try and browse the drive, it has a padlock on it and claims I don't have permission to display.  What is the correct way to plug in a second HD?

 gedit /etc/fstab reports
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

fdisk reports
trad@UbuntuLinux:~$ sudo fdisk -l
Password:

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9588    77015578+  83  Linux
/dev/hda2            9589        9729     1132582+   5  Extended
/dev/hda5            9589        9729     1132551   82  Linux swap / Solaris

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14592   117210208+   7  HPFS/NTFS
trad@UbuntuLinux:~$

---

### Post by kidders on 2006-09-05
Hi there,

You may be misunderstanding how your storage devices are handled in Linux. /etc/fstab doesn't *report* anything ... it's where you tell Ubuntu what to expect. So, if you tell it you have an optical drive there, it will believe you!

In general, all you need to do is the following:

[LIST=1]
[*]Add your new hard disk.
[*]As you've done already, identify it's /dev entry with, say, fdisk.
[*]Repartition + format your new disk as necessary.
[*]Make a new mountpoint
[*]Adjust /etc/fstab.
[*]Manually do what /etc/fstab tells Ubuntu to do during startup, to save having to reboot.
[/LIST]

So, let's say your new disk is at /dev/hdc and that you've used fdisk to make one huge partition on it, formatted to ReiserFS. First, create someplace to mount it, such as /mnt/extradisk. Then, remove any references to /dev/hdc from your /etc/fstab and add:

```

/dev/hdc1 /mnt/extradisk reiserfs defaults 0 0

```

Once you're done, use **sudo mount /mnt/extradisk** to mount it for the first time.

All done :-) although you *may* need to re-login to KDE/Gnome for them to realise new things have appeared.

---

### Post by tr0910 on 2006-09-06
Thanks, now I have the new drive wiped and partitioned FAT32 with reiserfs and am off to learn about user permissions, since I seem to denied access to most everything.  Is this common?

(This new drive is still padlocked in Nautilus.)

regards
Tim

---

### Post by kidders on 2006-09-06
FAT32 with ReiserFS? U lost me there :-(

The "padlock" is part of Linux's charm though! By very severely restricting the number of places ordinary users are allowed to put things, your computer is pretty much guaranteed never to fall victim to an accidental bungle or a virus. Normally, you should only ever try to put stuff in /tmp or your own home directory. Of course, if you wanted to, you could mount your extra hard drive in your home ... or even replace your home with it altogether.

Either way, you'll need to bear permissions in mind. To be allowed to write things on your second disk drive, you have to explicitly grant yourself permission to do so. All of these will have that effect, depending on how you want to achieve it, assuming "username" is your username and "/mnt/newdisk" is where your new disk drive is mounted:

**chown username /mnt/newdisk**
**chmod 777 /mnt/newdisk**
**chgrp admin /mnt/newdisk && chmod g+w /mnt/newdisk**
**chgrp username /mnt/newdisk && chmod g+w /mnt/newdisk**

---

### Post by TyphoonJoe on 2006-09-06
Tim-

I think you need -R so it gets all files and directories, not just the root directory of the filesystem. 

If you want your user account to "own" all the files and directories under a directory you can run: 
sudo chown -R username /path/to/directory
 (The -R makes it recursive)

Whereas this command will simply allow ALL users on the system to read/write/execute any file in this directory.  This seems like overkill, unless you have many users and don't care about security:
sudo chmod -R 777 /mnt/newdisk

Been away for linux a bit, could be wrong, could help ^_^

---

### Post by kidders on 2006-09-06
Nope ... you're exactly right :-)

---

