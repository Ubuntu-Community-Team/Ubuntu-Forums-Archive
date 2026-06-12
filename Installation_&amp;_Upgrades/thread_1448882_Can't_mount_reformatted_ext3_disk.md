---
title: "Can't mount reformatted ext3 disk"
date: 2010-04-07
forum: Installation &amp; Upgrades
---

### Post by myosotis on 2010-04-07
I'm fairly new to Ubuntu and I'm running Karmic Koala. I just reformatted an NTFS partition to Ext3, as I no longer need to access is from my windows installation. Now I'm unable to mount it though, and I get the message:

Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda6 on /media/DATA2 (DATA2 being the name of the previous NTFS partition. Now the label is linuxdata)

When I try to mount it using sudo in terminal I get the following message if I use the label DATA2:

NTFS signature is missing.
Failed to mount '/dev/sda6': Ogiltigt argument
The device '/dev/sda6' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

And if I use the label linuxdata:
mount: can't find /media/linuxdata in /etc/fstab or /etc/mtab

I've tried to search for help, but been unable to find an explanation.

---

### Post by vanadium on 2010-04-07
Post the output here of the commands

```

sudo fdisk -l
sudo blkid

```

This will tell us how your system sees the partition, and allow us to tell you how it can be mounted on the command line. By default, only the administrator can mount a partition in linux.

---

### Post by myosotis on 2010-04-07
Apologies for this being in Swedish. I'll translate if necessary.

from fdisk -l

Disk /dev/sda: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x4912b98e

    Enhet Start     Början        ****     Block    Id  System
/dev/sda1               1        1274    10233373+  12  Compaq-diagnostik
/dev/sda2   *        1275       10383    73162752    6  FAT16
/dev/sda3           10383       12207    14648437+  83  Linux
/dev/sda4           12208       19457    58235625    5  Utökad
/dev/sda5           12208       12449     1943833+  82  Linux växling / Solaris
/dev/sda6           12450       19457    56291728+  83  Linux

Disk /dev/sdb: 160,0 GB, 160041885696 byte
255 huvuden, 63 sektorer/spår, 19457 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0x4912b98f

    Enhet Start     Början        ****     Block    Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdc: 1000,2 GB, 1000204886016 byte
255 huvuden, 63 sektorer/spår, 121601 cylindrar
Enheter = cylindrar av 16065 · 512 = 8225280 byte
Diskidentifierare: 0xe8900690

    Enhet Start     Början        ****     Block    Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS



and from sudo blkid

/dev/sda1: UUID="CAB4CFE6E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="CA18493318492035" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="d0ea03ac-1bd7-4070-bcb0-272b9e9ebd69" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="0ef37d66-684a-409e-a87e-66623c2a4aba" TYPE="swap" 
/dev/sda6: LABEL="linuxdata" UUID="8689a603-464a-4a54-b3f5-b4650cfd9335" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: UUID="16E0BFE1E0BFC4F1" LABEL="DATA" TYPE="ntfs" 
/dev/sdc1: UUID="3A902FF2902FB2F5" LABEL="Kameleont" TYPE="ntfs"

---

### Post by vanadium on 2010-04-07
No problem for Ubuntu speaking swedish ;) Not that i know any, but the output is familiar nevertheless.

Both fdisk -l and blkid consistently report your partition /dev/sda6 as a linux formatted partition. blkid believes it is ext3.

You should perhaps have reported the complete mount commands you used. Normally, the mount command should automatically recognize the file system. Anyway, try this:

```

sudo mount -t ext3 /dev/sda6 on /media/DATA2

```

If still a problem, I'd try to format it once more:

```

sudo mkfs -t ext3 -L linuxdata /dev/sda6

```

---

### Post by myosotis on 2010-04-07
Ha, yes, the Swedish is impressive. :)

And after reformatting everything seems to work! I still don't understand why the mount point is still called DATA2, like the NTFS partition, even though it's now called linuxdata (and shows up in Nautilus under that name). But as long as it works I'm happy. Thank you!

---

### Post by myosotis on 2010-04-08
Hm, no actually the problem is still there, or maybe I'm missing something. I manage to mount the disk using  the mount command you wrote, but then at reboot I have to do the same thing again. I've tried to change permissions to my user, as well as changing the group to my user, but that doesn't work. Ideally I'd like it to automount on startup.

---

### Post by vanadium on 2010-04-08
> I still don't understand why the mount point is still called DATA2, like the NTFS partition,
The moint point is an existing directory on your drive. You choose which mount point to use.

To have the drive auto mount on startup, you need to include it in /etc/fstab.

1) Create an appropriate mount point
```

sudo mkdir /mnt/linuxdata

```

2) Determine the uuid of the drive
```

sudo blkid

```
Copy the part UUID=" ...." for your partition (/dev/sda6) to the clipboard

3) Open /etc/fstab in an editor with root permissions
```

gksudo gedit /etc/fstab

```

The file now opens. Add a line that reads like

```

UUID=" ..." /mnt/linuxdata ext3 defaults 0 2

```
where you substitute the UUID= ... information from step 2. Save the file and exit the editor.

4) Mount and test if all is good:
```

sudo mount -a

```
There should be no output here! Otherwise, you made an error. If there is no output, you can now navigate to /mnt/linuxdata to see the contents of your drive. The drive will automount at startup.

By default, you won't be able to write on the drive. Also, access is not quite easy (having to mount to /mnt first).

* To ease access, create a link in your home directory. Open two windows of navigator. Navigate in the left one to /mnt. Press Ctrl+Shift and drag "linuxdata" from the left to the right pane. Now, a symbolic link is created in the right pane that acts and feels like a real directory.

* Give full permissions to yourself as user
```

sudo chown $USER:$USER /mnt/linuxdata

```
(you can also do this graphically using a nautilus window with root permissions).

Now the drive is all yours.

---

### Post by psusi on 2010-04-08
It sounds like you added the partition to your /etc/fstab before you reformatted it.  Remove the line for it from /etc/fstab.

---

### Post by myosotis on 2010-04-08
I still don't get it to work.

I created /mnt/linuxdata. (Does it matter that my other mount points seems to be under /media/?)

The blkid gives me:

```
/dev/sda1: UUID="CAB4CFE6E49BED2A" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="CA18493318492035" LABEL="ACER" TYPE="ntfs" 
/dev/sda3: UUID="d0ea03ac-1bd7-4070-bcb0-272b9e9ebd69" TYPE="ext3" 
/dev/sda5: UUID="0ef37d66-684a-409e-a87e-66623c2a4aba" TYPE="swap" 
/dev/sda6: LABEL="linuxdata" UUID="e5d787ef-5ee0-4d59-9ee2-ea104653e1ce" TYPE="ext3" 
/dev/sdb1: UUID="16E0BFE1E0BFC4F1" LABEL="DATA" TYPE="ntfs" 
/dev/sdc1: UUID="3A902FF2902FB2F5" LABEL="Kameleont" TYPE="ntfs" 
```

So I changed the fstab to:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=d0ea03ac-1bd7-4070-bcb0-272b9e9ebd69 / ext3 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=0ef37d66-684a-409e-a87e-66623c2a4aba none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/DATA2 ntfs-3g defaults,locale=sv_SE.UTF-8 0 0
/dev/sdb1 /media/DATA ntfs-3g defaults,locale=sv_SE.UTF-8 0 0
UUID=e5d787ef-5ee0-4d59-9ee2-ea104653e1ce /mnt/linuxdata ext3 defaults 0 2
```

When mounting that gave me the error:

```
NTFS signature is missing.
Failed to mount '/dev/sda6': Ogiltigt argument
The device '/dev/sda6' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
```

So then I changed the fstab to:

```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda3 :
UUID=d0ea03ac-1bd7-4070-bcb0-272b9e9ebd69 / ext3 errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=0ef37d66-684a-409e-a87e-66623c2a4aba none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sdb1 /media/DATA ntfs-3g defaults,locale=sv_SE.UTF-8 0 0
# Entry for /dev/sda6 :
UUID=e5d787ef-5ee0-4d59-9ee2-ea104653e1ce /mnt/linuxdata ext3 defaults 0 2
```

Now I don't get errors but it still won't mount, and doesn't show up in Nautilus at all.

---

### Post by myosotis on 2010-04-08
Correction: It does mount, but it doesn't show up among the mounted disks in Nautilus, which confused me. Is it not supposed to? But with the symbolic link it works well, of course.

---

### Post by psusi on 2010-04-08
REMOVE the line from fstab entirely.  It isn't showing up in nautilus because it only shows things mounted under /media.  If you get rid of the line completely then it will still show up and be mounted automatically when you open it.

---

### Post by vanadium on 2010-04-09
It is indeed your choice.

Either remove the line as psusi said. An icon will appear and it will be mounted when you click the icon (but only then!)

Keep the line, and it will be mounted automatically upon startup. However, it is transparently part of your file system: it feels and behaves as a part of your file system and has no separate "drive" icon. Then you can use shortcuts wherever you want to access the partition, or directories on it, easily the way you want.

Its your choice.

---

