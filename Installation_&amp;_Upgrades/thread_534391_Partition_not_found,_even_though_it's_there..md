---
title: "Partition not found, even though it's there."
date: 2007-08-25
forum: Installation &amp; Upgrades
---

### Post by cochon on 2007-08-25
Ubuntu is telling me I cannot open /dev/sdb1 I have tried manually as root.

I have just installed Ubuntu 7.04 (was running Windows XP).  There are no problems with the partition as far as I can tell, I can access all the files no problem from live cds or the windows install.

Gparted looks like this:
[IMG]http://img340.imageshack.us/img340/9524/screenshotinformationabhh7.png[/IMG]

Any ideas?  This is a massive headache as all my documents etc are stored on this drive.  The main thing I don't understand is how this partition can exist and be seen by gnome partition editor as /dev/sdb1 but /dev/sdb1:No such file or directory

Pretty strange huh?

---

### Post by meznaric on 2007-08-25
What happens if you try to mount it with the mount commad?

---

### Post by cochon on 2007-08-25
Same message I get from everything else
```
# mount /dev/sdb1 /media/sdb1
mount: special device /dev/sdb1 does not exist
```

---

### Post by merlinus on 2007-08-25
Preface the mount command with sudo.

-merlin

---

### Post by cochon on 2007-08-25
I was doing it as root.

---

### Post by merlinus on 2007-08-25
Give it one more try:

```

sudo mount /dev/sdb1 /media/sdb1 -t vfat iocharset=utf8,umask=000 0 0

```

Just to be sure, you did create the mountpoint?

-merlin

---

### Post by cochon on 2007-08-26
Yeah 1st thing I did was make the mountpoint.  

The command you gave me does the following (not that I like printing large amounts of text with no actual errors I can see but here goes...)

```
mirf@taku:~$ sudo mount /dev/sdb1 /media/sdb1 -t vfat iocharset=utf8,umask=000 0 0
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

```

I did a sudo su and ran the command again, taking sudo off the front and the same thing happened.

Just to add, I have tried many different mount commands and even played with fstab trying to add the partition there.  The problem is that according to mount /dev/sb1 does not exist.  Even though it clearly does :)

---

### Post by cochon on 2007-08-26
OK I've got some tantalising new info here....  I did fdisk -l and just look what I get for /dev/sdb !

```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?           1       38913   312568641    c  W95 FAT32 (LBA)
```

I guess I gotta rbeuild the partition table for the drive, but I don't want to lose any data.  Any ideas?

edit: Thinking about this, there must be another explanation.... Why else would I be able to read this drive from live cds and windows but not Ubuntu?  Ubuntu handles hard drives differently?  I know there is this UID business going on with Ubuntu hardware but I don't think that's the problem.

---

### Post by merlinus on 2007-08-26
Did you try

sudo mount -t vfat /dev/sdb1 /media/sdb1

-merlin

---

### Post by merlinus on 2007-08-26
You can try this for rebuilding the partition table:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

More info here:

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

-merlin

---

### Post by brosher on 2007-08-28
Did you get this figured out?  I just upgraded and have the same problem.  I can't mount anything.  Same message:

special device /dev/hdb6 does not exist

---

### Post by merlinus on 2007-08-28
You might post output of:

```

sudo fdisk -l
mount
cat /etc/fstab

```

-merlin

---

### Post by cochon on 2007-08-29
The only mention of /dev/sdb in any of the last commands you entered is with fdisk -l

sdb does not show up in fstab and of course it is not mounted so mount doesn't show it up either.

In a way I'm glad someone else has this problem.  But it's a bummer ubuntu won't play nice with the partition.  I wondered at first if it might be something to do with the LBA flag being set but I can't see why this would cause any problems really.

Merlin thanks for those links re Partition table stuff... I'll check them out later however I'd rather figure out what it is that's causing Ubuntu to ignore the partition rather than change it.  I will edit partition data as a last resort.

---

