---
title: "I need imediate help"
date: 2006-07-05
forum: Installation &amp; Upgrades
---

### Post by valon on 2006-07-05
Hi.

I recieved the Ubuntu disks yesterday and decided to install it.

I first downloaded Partition Magic (7 or 8) and made a partition. Then it asked me to restart my pc. So i did and then it started doing the partition processes at a blue screen (partition magic)... it got to about 31 % total then it froze. And windows restarted by itself but it gets to the windows logo screen with the trail going back and forth then it restarts again. It goes to the windows did not start correctly the previous time what do you want to do; and the options display. I have the XP cd... What should I do?

---

### Post by taurus on 2006-07-05
Well, sounds to me like partition magic somehow screwed up your partition table!  Since you have an XP disc, the easiest way is to reinstall XP.  Don't forget to create an empty partition for Ubuntu later...  Otherwise, you can boot the Ubuntu CD (as LiveCD) and see if you can use gparted to resize or fix your partition table.

---

### Post by valon on 2006-07-05
uh
I have so much stuff on xp that I don't want to loose.
I was thinking of botting xp by command prompt and fixing the important files by scanning the disk and fixing the messed up files.

btw im using ubuntu right now. (as a live cd)

---

### Post by aysiu on 2006-07-05
You can mount your Windows partition from the live CD. You can't modify any files, but you can certainly back up the important ones.

This terminal command will tell you what your partition table looks like: ```
sudo fdisk -l
``` We'll assume, for this example, that your NTFS partition is /dev/hda1 ```
sudo mkdir /recovery
sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222 0 0
``` You may want to copy and paste those commands instead of retyping them. Then go to the /recovery directory, and you should see your Windows XP files.

Now... if your partition table is corrupted... i.e., you don't have one.. well, that's going to be problematic, but there are fixes for that, too.

---

### Post by valon on 2006-07-05
following those codes here's what i got

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        4997    40138371    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /recovery
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /recovery -o nls=utf8,umask=0222 0 0
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by valon on 2006-07-05
here's what my hd looks like

[http://img337.imageshack.us/img337/7864/screenshot7ae.jpg](http://img337.imageshack.us/img337/7864/screenshot7ae.jpg)

---

### Post by aysiu on 2006-07-05
That's weird. Maybe I messed up the options somehow? Let's try something else then, something simpler: ```
sudo mount -t ntfs /dev/hda1 /recovery
gksudo nautilus
``` [quote=valon]
here's what my hd looks like

[http://img337.imageshack.us/img337/7...eenshot7ae.jpg](http://img337.imageshack.us/img337/7...eenshot7ae.jpg)[/quote] That's good. That means your partition table is intact, so we can probably save your files.

---

### Post by valon on 2006-07-05
ubuntu@ubuntu:~$ sudo mount -t ntfs /dev/hda1 /recovery
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$ gksudo nautilus

(nautilus:7909): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

---

### Post by aysiu on 2006-07-05
Okay. False hope. I guess your partition table may, in fact, be damaged.

Incidentally, when you ran ```
gksudo nautilus
``` did the file manager come up or not?

Unless someone else has a brilliant idea, [this link](http://geekblog.oneandoneis2.org/index.php?m=200602) may help. Do a find-in-page search for *gpart*. Best of luck.

---

### Post by valon on 2006-07-05
root folder opens up with a "Desktop' Icon

---

### Post by aysiu on 2006-07-05
[QUOTE=valon]root folder opens up with a "Desktop' Icon[/QUOTE]
Well, at least *something*'s working, then.

It appears that even though the partition table recognizes your drive as NTFS at /dev/hda1, the partition is damaged in some way that doesn't allow us to mount it for recovery purposes.

---

### Post by valon on 2006-07-05
that sucks.

Is there anything that can be done?

---

### Post by aysiu on 2006-07-05
[QUOTE=valon]that sucks.

Is there anything that can be done?[/QUOTE]
There's [this links](http://geekblog.oneandoneis2.org/index.php?m=200602) I referred to you earlier, which talks about using GPart.

There's also something called TestDisk, which I know has worked for some people:
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I have not used either of these programs myself, though.

---

### Post by valon on 2006-07-05
The testdisk seems like the one for the job but when i download it... half of the ones I download don't open and the 'static' one that opens does not start (the program)...

So i decided to run mepis and try that same here on here... except now even the 'static' version will not unpack or install.

Is there anyway around this?

---

### Post by valon on 2006-07-05
I get this messege all the time

<root/Desktop/testdisk-6.4-1.src(3).rpm';echo RESULT=$?
warning: //root/Desktop/testdisk-6.4-1.src(3).rpm: Header V3 DSA signature: NOKEY, key ID eaaeee88
error: cannot write to %sourcedir /usr/src/rpm/SOURCES
RESULT=1

---

