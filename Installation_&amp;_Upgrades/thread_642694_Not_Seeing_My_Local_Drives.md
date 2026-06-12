---
title: "Not Seeing My Local Drives"
date: 2007-12-16
forum: Installation &amp; Upgrades
---

### Post by techgeek40 on 2007-12-16
Okay - I have done it - finally.
I got away from the EasyBCD - and redid the system.

I had to (LOL) one of my hard drives crashed out.

But, be that as it may - I loaded XP (twice - on two partitions)
I left XP on partition one alone - updated XP on partiton two to Vista
Made sure I had a partition for Ubuntu -

Edited the grub - now can boot into Ubuntu or Vista/XP without EasyBCD

But - in Ubuntu I can't see my other drives :<

Hell, I'm not even sure where to go to try to find them.

How can I have either my other drives (three all told) on the desktop or use a "windows browser" (for want of a better word) to find them - or how can I get them to "mount"

---

### Post by confused57 on 2007-12-17
This guide might help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you mount your Windows partition in /media/windows(sudo mkdir /media/windows), instead of /windows, as the guide suggests, you should get an icon on the desktop for the partition.

Here's a utility that you can install in XP to see your Ubuntu drive:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
don't think it works in Vista?

---

### Post by techgeek40 on 2007-12-17
I tried that guide - but it looks nothing like what I have
I can't even see my CD ROM or my (C - VISTA) drive

Here is what I have from the terminal window.
Now the goofy thing is this: If I run KDE I can't find the drives (either on desktop or in a "browser window")
Unless there is a way to get there from a browser window.

BUT if I go into a Gnome desktop - I see the Vista drive and the flash drive (tough not the CD rom - unless I open and close the drive with a disk in there)

Below is the information I have

THIS IS THE SUDO FDISK -L ((I TYPED THIS ALL LOWER CASE)

techgeek@nerds-02:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5992    48130708+   7  HPFS/NTFS
/dev/sda2            5993        6235     1951897+  82  Linux swap / Solaris
/dev/sda3            6236        7296     8522482+  83  Linux

Disk /dev/sdb: 1021 MB, 1021125120 bytes
255 heads, 63 sectors/track, 124 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00a7ad99

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         124      995998+   b  W95 FAT32
techgeek@nerds-02:~$ 
techgeek@nerds-02:~$ 


THIS IS THE SUDO NANO /ETC/FSTAB (I TYPED THIS ALL LOWER CASE)


GNU nano 2.0.6              File: /etc/fstab                                  

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=9fdc0494-f56d-4d55-bc21-cd5a445437c1 /               ext3    defaults,erro$
# /dev/sda1
UUID=AA9C68C09C6888A1 /media/sda1     ntfs    defaults,umask=007,gid=46 0      $
# /dev/sda2
UUID=e67ea269-47c2-4119-a422-ad7a32646955 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

---

### Post by jmink78 on 2007-12-18
I just had this same problem. I used the psychonauts page to walk through the re-mount process, and at the end I received an error stating my windows drives were in a hibernate state. Definitely a noob move on my part, but you may want to run the following command and check the output for the hibernate error:

```
sudo mount -a
```

Here is the output that I received to indicate the Windows partition was not shut down properly:

Failed to mount '/dev/sda1': Operation not permitted
The NTFS partition is hibernated. Please resume and shutdown Windows
properly, so mounting could be done safely.
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 /media/sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 /media/sda3 ntfs-3g defaults,force 0 0
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

---

### Post by vanadium on 2007-12-18
/dev/sdb1 is not in /etc/fstab, so it is normal that it is not mounted. /dev/sda1, your ntfs volume, is in /etc/fstab, and I see two possibilities why it would not be mounted: 1) see post of jmink78: your ntfs volume is "unclean" and needs to be checked; 2) during reinstallation of Windows, you reformatted the disk and that would cause the UUID to change. Run the command "blkid" and see whether the UUID listed corresponds with the one in /etc/fstab. If not, replace with the correct uuid (you can just copy the UUID=... from the output of the command and paste over the old UUID= entry in your /etc/fstab). As allways, make a backup copy of your /etc/fstab first.

---

### Post by confused57 on 2007-12-19
Your fdisk -l & /etc/fstab outputs are showing only an NTFS partition on /dev/sda1.

> Here is what I have from the terminal window.
Now the goofy thing is this: If I run KDE I can't find the drives (either on desktop or in a "browser window")
Unless there is a way to get there from a browser window.

BUT if I go into a Gnome desktop - I see the Vista drive and the flash drive (tough not the CD rom - unless I open and close the drive with a disk in there)

In Kubuntu,have you tried clicking on the Konqueror Web Browser in the main panel, then selecting "Storage Media" to see if your sda1 partition is listed.

Flash drives and cd drives are automounted, plugging in the flash drive or inserting a disk in the cdrom will mount the drive & place an icon on the desktop.  Your cdrom won't have an icon, unless you insert a disk.  I believe the flash drive is mounted, if you boot your pc with the drive inserted.

---

