---
title: "optimizing xubuntu on two hard drives"
date: 2008-02-29
forum: Installation &amp; Upgrades
---

### Post by rolypolycat on 2008-02-29
Hello!

This isn't anything really earth-shaking, but I'm  just curious, and I couldn't find info about this topic exactly.
I recently installed Xubuntu(gutsy gibbon), as a fresh install. I have a little 4gb hard drive, and a large 160 gig drive. I put root on the little drive, and /home on the big one. I think the swap file is there, too, but I'm not sure exactly where it ended up after I partitioned everything. This is a sample of the fdisk -l command in my terminal:
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units= cylinders of 16065 * 512 =8225280 bytes
Disk Identifier: 0x000ebb0f

Device      Boot      Start      End           Blocks              ID     System
/dev/sda2   *           1             19457      1562883215      5      extended
/dev/sda5                 1            188          1510015+         82     linux swap/ solaris
/dev/sda6                 189        19547       154778211        83    linux

Disk /dev/sdb: 4321 MB 4321787904 bytes
255 heads, 63 sectors/tracks,525 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk Identifier= 0x03150314

I have the little drive on it's own cable, marked master; the other drive and my dvd burner are on a dual cable, with the hard drive marked master and the dvd drive marked slave.

Basically what I'm asking is: is this the best arrangement for  optimizing xubuntu on a 5 year old Compaq 4400 presario? And is the swap file on the big drive or the little one? Will , or should, it share the same drive as the root files?  I set things up this way so if I needed to re-install after my niece manages to download  some crud from Myspace, or if things just go wonky, I can re-install without trashing my /home directory in the process. Or the Master Boot Record.Or the swap file. Or anything else vital to Linux:) I'm not exactly a newbie, but when it comes to reading the info above, I'm out of my league. (in fact, I'm not even sure if the MBR is on the little root drive, or stashed on the /home drive; can someone tell where it is from this info? And if I should move it if it's in danger from a future re-install?)
Thanks for any and all help anyone can give me. Once again, i apologize for asking what I guess is a trivial question, but I couldn't find any info on this situation, just dual-boots with Windoze. And I do want to learn more about Linux besides just software. Thanks again!

---

### Post by bapoumba on 2008-03-01
Hello :)
From what I see above, I'd say everything is on the big drive:
```
**Disk /dev/sda: 160.0 GB**, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units= cylinders of 16065 * 512 =8225280 bytes
Disk Identifier: 0x000ebb0f

Device Boot Start End Blocks ID System
**/dev/sda2** * 1 19457 1562883215 5 extended
**/dev/sda5** 1 188 1510015+ 82 linux swap/ solaris
**/dev/sda6** 189 19547 154778211 83 linux
```

Unless some lines are missing under that section:
```
**Disk /dev/sdb: 4321 MB** 4321787904 bytes
255 heads, 63 sectors/tracks,525 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk Identifier= 0x03150314
```

But I'm not sure why your boot sector is on a partition labeled "extended" (I always place mine on the root partition).

---

### Post by rolypolycat on 2008-03-01
Hello!

I just re-ran the fdisk -l command. There is a line missing. Just below the last listin of disk sdb1 is this line:
Device         Boot      Start            End          Blocks          ID            System
/dev/sdb1                      1                525        4217031       83            Linux

I didn't notice that before; I have to use aterm on xubuntu because the terminal that comes with it has a bug (it terminates the session), and aterm won't let me copy and paste. But from what you say, and what I've read in Ubuntu Linux Toolbox, the * means that disk is the boot disk, right? So if it's on the big disk, how do I remove it to the little one? And does this mean my /root isn't on the little disk, either?:confused:
 I want to keep /home and /root separate for upgrades, re-installs, etc. Any advice on moving, either, both or none is appreciated. Thanks!

---

### Post by bapoumba on 2008-03-01
For the terminal, try <alt-F2> and run ```
xfce4-terminal
```. If it works properly, you can add a new item on a panel with the command to launch it.
To copy and paste from and to a terminal, you have to use either:
- <shift><ctrl><c> and  <shift><ctrl><v> (as <ctrl><c> has a special meaning in the terminal)
- middle mouse clic to paste something highlighted in an open window

I'm not sure you can move the boot sector to another partition without reformating. You could just go this way until you fresh install hardy, for ex, and place it on a primary partition. Do not break a working setup ^^

To know which is what:
```
cat /etc/fstab
```

Although with only one drive, this is also the setup I have, with a separate /home partition (created with the very first warty image that got released ;)):

---

### Post by rolypolycat on 2008-03-01
Hello!

Well, I typed in the terminal command, and was promptly restarted; guess they still haven't fixed that stupid bug yet. Oh well.
This is a fresh install of gutsy; I haven't even replaced my stuff in the home folder yet. Reformatting wouldn't be a problem. 
So if I did a re-install, when it asks for a place to put /root, I'd use /sdb instead of sda? I wonder how the little drive got changed to sdb? It's on a separate cable alone, marked as master; shouldn't that be sda? And would the mbr then end up where it's supposed to, in the root disk?:confused:
Sorry for so many questions; I'm self-taught, and I don't find much info in my linux books on the hardware aspect of linux, just software.I guess that's a more advanced topic.:)
Thanks again!!

---

### Post by rolypolycat on 2008-03-02
Thanks for the terminal tip! Here's my fstab file:

shell@the-cathouse:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=be0bf06c-2b23-4575-b1b1-59c2a80b1ac2 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda6
UUID=53b67379-abfc-4967-ba4c-f2a21bda2bb9 /home           ext3    defaults        0       2
# /dev/sda5
UUID=0483fb44-f6b1-4ffc-be39-5441129d6ffa none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Any idea what this stuff means? And what's that about an error on line 6?:confused: Is that something I should be concerned about; something's wrong in my filesystem?
I hope this helps. Thanks!

---

### Post by louieb on 2008-03-02
One thing you might think about is putting both hard-drives on the same cable. Mixing an optical-drive and a hard-drive on the same cable can slow the hard-drive down. 

After you make the change you could fix your fstab and grub menu. But a reinstall would be less frustrating . 

One last thing I find the **mount** command useful Run without any options it will list what is mounted where. But it just doesn't list where swap  is mounted.
>  Any idea what this stuff means? And what's that about an error on line 6?
Its normal.  Just a parameter to mount the partition read only in case of an error.

---

### Post by torgrot on 2008-03-02
If it were doing it, I would probably just get rid of the 4GB drive completely.  It would probably slow the bigger drive down almost as much as the DVD on the same cable.  I would put the 160GB drive on one cable as master and then just reinstall.

torgrot

---

### Post by bapoumba on 2008-03-02
> **rolypolycat said:**
> Thanks for the terminal tip! Here's my fstab file:

shell@the-cathouse:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
#** /dev/sdb1**
UUID=be0bf06c-2b23-4575-b1b1-59c2a80b1ac2 **/**               ext3    defaults,errors=remount-ro 0       1
# **/dev/sda6**
UUID=53b67379-abfc-4967-ba4c-f2a21bda2bb9** /home**           ext3    defaults        0       2
#** /dev/sda5**
UUID=0483fb44-f6b1-4ffc-be39-5441129d6ffa none            **swap**    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

Any idea what this stuff means? And what's that about an error on line 6?:confused: Is that something I should be concerned about; something's wrong in my filesystem?
I hope this helps. Thanks!
The system (/) is on sdb, which is the little drive (if there are errors, it will be mounted as read-only to be checked and fixed).
/home and swap are on sda, the big drive.

I'm not much into hardware, so I'll go with what has been suggested above. And may be wait for next reinstall to change everything.

---

### Post by johnlvs2run on 2008-05-21
> **torgrot said:**
> If it were doing it, I would probably just get rid of the 4GB drive completely.  It would probably slow the bigger drive down almost as much as the DVD on the same cable.  I would put the 160GB drive on one cable as master and then just reinstall.

Why not use the 4gb drive as the swap file.

Wouldn't this be faster than having the swap on the same drive as the files.

---

