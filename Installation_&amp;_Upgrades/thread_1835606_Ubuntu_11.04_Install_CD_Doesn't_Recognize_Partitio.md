---
title: "Ubuntu 11.04 Install CD Doesn't Recognize Partitions"
date: 2011-08-29
forum: Installation &amp; Upgrades
---

### Post by drucifer on 2011-08-29
I'm having trouble installing Ubuntu in my Dell Inspiron 630m.

I inherited this laptop, and it was full of evil, evil software. So, immediately upon getting it, I installed Natty Narwhal.  For a whole week, I've been successfully dual-booting Ubuntu 11.04 and Windows XP as I cleaned the computer up--no problemo.  But yesterday, I decided to do a fresh install of Windows XP Pro, and that's when everything went wrong.  XP now works fine, but as is the wont of Windows, it blew Linux away.  When I go to re-install Linux, the live CD does not recognize any partitions on the harddrive at all; in fact, it seems to think that the entire harddrive is unformatted.  The same goes for GParted.


I've looked at previous posts regarding partition problems upon install, but I can't find any solutions that really fit the bill.  I've defragmented my Windows partition to no avail, and fdisk knows that the partitions are there (see the output below). When reading the fdisk output, it looks to me like I have a corrupted partition table, which I would have no clue how to fix.  Any help here would be much appreciated--anything, anything that might save me from the horror of primarily proprietary bootage :|

```
ubuntu@ubuntu:~$ sudo fdisk -lu
omitting empty partition (5)

Disk /dev/sda: 78.7 GB, 78732380160 bytes
255 heads, 63 sectors/track, 9572 cylinders, total 153774180 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   128262959    64131448+   7  HPFS/NTFS
/dev/sda2       128278526   153772031    12746753    5  Extended
/dev/sda3       149600256   153772031     2085888   82  Linux swap / Solaris
/dev/sda5       128278528   145424383     8572928   83  Linux
/dev/sda6       145426432   149598207     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 1048 MB, 1048051712 bytes
33 heads, 61 sectors/track, 1016 cylinders, total 2046976 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6f20736b

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   778135908  1919645538   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(386555, 11, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(953624, 6, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   168689522  2104717761   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(83800, 2, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1045562, 23, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?  1869881465  3805909656   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(928902, 28, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1890665, 16, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdb4   ?           0  3637226495  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1806868, 19, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
```

---

### Post by drucifer on 2011-09-01
Bump.

---

### Post by Hakunka-Matata on 2011-09-02
**EDIT:  Never mind, go to post #6**

You have 65+ GiB for Windows and only 13+ for all your Linux partitions.

[LIST]
[*]there are two swap partitions, only need one
[*]the windows NTFS partiton should be shrunk and the Extended partition enlarged, allowing enough room for a reasonable Linux system.
[*]But before you do anything else, please post the output of ```
sudo sfdisk -luM
``` I don't know if that will work if you're using liveCD if not repost the output of ```
sudo fdisk -lu
```
[*]It would be great to see a screenshot of gparted's view of your disk too.
[*]do you know how to take and post a screenshot? (no offense intended, only asking)
[/LIST]
[B]
/dev/sda[/B]            [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]153,774,180[/FONT] *             512 =             **78,732,380,160             **

           blocks      |                sectors=blocks*2 |              sectors * 512 = bytes
            
                              **sda1**             [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]64131448[/FONT]             128,262,896 *            512 =             **65,670,602,752**             Primary – boot flag set – WindowsXP             
            
                              **sda2.**             [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]12746753[/FONT]             25,493,506             * 512 =             **13,052,675,072 **            Extended ID 5             
            
                              **sda3**             [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced][COLOR=Black]2085888[/COLOR][/FONT][COLOR=Red][COLOR=Black]             4,171,776             * 512 =            ** 2,135,949,312**             Logical – swap ID 82[/COLOR] **_sda3 is a primary, delete it_**[/COLOR]
            
                              **sda5**             [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]8572928[/FONT]             17,145,856             * 512 =             **8,778,678,272**             Logical – Linux  ID 83             
            
                              **sda6**             [FONT=Cumberland AMT,Cumberland,Courier New,Liberation Mono,Nimbus Mono L,DejaVu Sans Mono,Courier,Lucida Sans Typewriter,Lucida Typewriter,Monaco,Monospaced]2085888[/FONT]             4,171,776             * 512 =             **2,135,949,312 **            Logical – swap ID 82

---

### Post by Hakunka-Matata on 2011-09-02
**EDIT:  Overlapping partitions, sda2 & 3, both primary**

omitting empty partition (5)

that part bothers me

---

### Post by Hakunka-Matata on 2011-09-02
Overlapping partitions, **[COLOR=Red]sda2 & sda3 are overlapping: [/COLOR]** they're both primary partitions.  delete sda3.

Do me a favour, I'd like you to run ```
 sfdisk -luM 
``` and post the results before you fix it.  I want to see how sfdisk -luM reports the partitions.  thanks if you can.

Boot your liveCD/USB and open gparted, delete sda3, then we'll have a look at resizing

# sda1, 2, 3, & 4 are always primary partitions, even if you create sda1 as an extended, then create a logical inside that extended, it will be created as sda5, the first logical partition in the mapping.

---

### Post by maclinux on 2011-09-25
Hi. this is what i found out as well.  

renatohe@renatohe-1005PE:~$ sudo sfdisk -luM

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Units = mebibytes of 1048576 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start   End    MiB    #blocks   Id  System
/dev/sda1   *     1  102406- 102406- 104863263+   7  HPFS/NTFS
/dev/sda2     102401  107168   4768    4882432   82  Linux swap / Solaris
/dev/sda3     107169  238474  131306  134457344   83  Linux
/dev/sda4         0      -      0          0    0  Empty


but the gparted app says there are one whole unalocated partition and here is the pict to prove it

---

### Post by Hakunka-Matata on 2011-09-25
that's right, sda1 ends @ sector 102,406, and sda2 begins @ 102401, they are overlapping.  sda2 is a swap partition, fortunate.  Delete it and make a new one.

How to delete?, since GParted won't do it?  Is that a valid question?

---

### Post by oldfred on 2011-09-25
Not sure if testdisk would do it, sometimes it has issues also.

I would first backup partition table.

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

And since we can just delete sda2 I think we can edit a copy to PTsda.txt to zero out sda2 entries and read it back in. 

Post PTsda.txt

Using sfdisk to fix partition table problems - not without risk
[http://ubuntuforums.org/showthread.php?t=1192598](http://ubuntuforums.org/showthread.php?t=1192598)
```
sudo sfdisk --no-reread -f /dev/sdc -O PTsda.save < PTsda.txt
```
"--no-reread" means don't check if disk is unmounted
-f force
"-O PT.save" means save a backup of original partition table in PT.save. PT.save is in binary format.



This may also work.
this occasionally fixes issues and is worth trying:
you do the following :
fdisk /dev/sda
use option : x (expert mode)
use option : f (fix partition order)
use option : r (return)
use option : p (to print)
use option : v to verify partition
if it is ok
then you can do
option : w ( to write table to disk)
option : q to quit

Fix overlaping partition error srs5694
[http://ubuntuforums.org/showthread.php?t=1667614](http://ubuntuforums.org/showthread.php?t=1667614)

---

