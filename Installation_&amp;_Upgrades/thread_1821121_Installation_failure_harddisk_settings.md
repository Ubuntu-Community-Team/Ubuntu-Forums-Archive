---
title: "Installation failure harddisk settings"
date: 2011-08-08
forum: Installation &amp; Upgrades
---

### Post by redn123ax on 2011-08-08
Hello,

I tried to install ubuntu today, but i ran into a few problems.
I now fixed them all, except for one...

When i want to install ubuntu it first asks for a few things.
First it asked for the language. I selected dutch..
Then it asked if i want to install MP3 support and updates.
I selected them both.

Then there should be a screen where i can setup the partition settings ..
But it doesn't....

The setup gets stuck at the update-screen...

When i try system settings -> disk utility and i try to make a ext4 partition it also fails and give me this message:
```
an error occurred whil performing an operation on "500 GB Hard 
Disk"(ATA ST9500420AS): The daemon is being inhibited
```the details message:
```
The daemon is being inhibited
```Further details:
Im having a MSI GX740 Laptop (64-bit) with an 500 GB Harddisk:
[IMG]http://i154.photobucket.com/albums/s253/red123nax/harddisk.jpg[/IMG]
Disk0:
- 12 GB: OK, recovery partition
- 100 MB: OK, recovery partition
- 273,40 GB: OK, Startup partition -> Windows 7
- 160,64 GB: OK -> Data partition
- 19,63 GB: Not assigned -> want to install ubuntu on it

Does anyone know why this just doesn't work ??

Thanks in advance,
ReDNaX

---

### Post by Hakunka-Matata on 2011-08-08
Your disk has/had four [COLOR=Red]primary[/COLOR] (the maximum allowed) partitions.  There is no possibility of installing to the disk the way it is configured now.  I'll get back to you with some links that explain how to accomplish this, even if you already know how to do it.  Do you have windows recovery disks?  Is your important data backed up?

EDIT:  oops, your disk has also been converted to dynamic (logical), that must be converted back to type Basic before anything can be changed.  [COLOR=Red]Windows will automatically convert a disk to SFS/dynamic if a fifth primary partition is attempted.[/COLOR]

---

### Post by Hakunka-Matata on 2011-08-08
[SIZE=2][COLOR=Blue][Here]("http://ubuntuforums.org/showthread.php?t=1819577&highlight=convert+to+basic")[/COLOR][/SIZE] is a thread that explains it all.

---

### Post by redn123ax on 2011-08-09
So basically i should convert the data-partition to a basic partition and then it should be all fine?

---

### Post by Hakunka-Matata on 2011-08-09
Converting both dynamic partitions to type standaard/basic is required, yes.  The problem is that MicroSoft has partitioned your disk with four primary partitions, this prevents you from creating any new partitions.  The limit for primary partitions on MBR disks is 4.  So you must go through the process of converting, shinking, moving, and deleting at least one of those four existing partitions before you can proceed with creating the partitions necessary for Ubuntu.

You need to create one Extended partition (Extended is a primary type partition).  Extended partitions may contain many Logical partitions.  Within that extended partition you will create two logical partitions for the Ubuntu system.  You may want to create three, if you choose to keep your Ubuntu Data on a separate /home partition, many people choose this method.


[LIST]
[*]backup important data on external media
[*]ensure you have discs necessary to reinstall windows 7 in case everything goes pear shaped
[*]convert dynamic partitions to basic partitions [http://ubuntuforums.org/showthread.php?t=1819577&highlight=convert+to+basic](http://ubuntuforums.org/showthread.php?t=1819577&highlight=convert+to+basic)
[/LIST]
The hyperlink above explains the process better than I could explain it.  I would suggest you follow instructions in it.

---

### Post by redn123ax on 2011-08-09
OK, i already did everything..
This morning i downloaded MiniTool Partition Wizard and converted the logical partitions to basic.

I scared the **** out of me when my laptop didn't start :P.. i didn't make backups because i'm on holiday (the 'C:' partition wasn't set active)
After that i converted the 'D:'-partition and had no problems with installing Ubuntu..

So problem solved and many thanks for helping me !!

---

### Post by Hakunka-Matata on 2011-08-09
Wonderful, you're welcome

gooiedag

---

