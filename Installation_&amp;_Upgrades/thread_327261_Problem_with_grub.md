---
title: "Problem with grub"
date: 2006-12-28
forum: Installation &amp; Upgrades
---

### Post by sheine on 2006-12-28
I made a slight change in grub on a partition different from Ubuntu. Now when I log in to Ubuntu, the process stops and I must use Control-D to get into Ubuntu. During the login process, I am referred to a log which presumably tells me how to fix the problem. It reads as follows but means nothing to me:


fsck 1.39 (29-May-2006)
fsck.ext2: Unable to resolve 'UUID=8e03b8f6-a08d-4634-93ee-3a8105a3183e'
/dev/hdb1: clean, 104415/3155936 files, 1213568/6309520 blocks
fsck died with exit status 8

Is there a simple solution?

---

### Post by shane2peru on 2006-12-28
I really don't think this is a grub issue, although it could be related to what you altered in the menu.lst.  Can you post the output of this: ```
cat /etc/fstab
```  then also we will need the output of this: ```
sudo fdisk -l
```  That will give us an idea of where the problem is.  It appears as though you have a problem with the blocks of a partition, and need to fix the problem.  Post those outputs and lets see if we can figure this out.  Also if you can let us know what you changed in your grub, we can see if that has any relation.  

Shane

---

### Post by sheine on 2006-12-28
You asked for it.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3
UUID=1e45b768-986e-44de-be73-74dd8d83586a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=DACC3491CC3469C1 /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=F09CA5C69CA587A4 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=24042D22042CF886 /media/hda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda7
UUID=8e03b8f6-a08d-4634-93ee-3a8105a3183e /media/hda7     ext2    defaults        0       2
# /dev/hdb1
UUID=db161597-e478-4c16-a0cc-a4787fb3ca34 /media/hdb1     ext3    defaults        0       2
# /dev/hdb2
UUID=0508c5a7-7071-4174-95fa-d2d331d63663 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0




Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            2519        4100    12707415    f  W95 Ext'd (LBA)
/dev/hda3            4109        4865     6080602+  83  Linux
/dev/hda4            1913        2518     4867695   83  Linux
/dev/hda5            2550        3059     4096543+   7  HPFS/NTFS
/dev/hda6            3060        4100     8361801   83  Linux
/dev/hda7            2519        2549      248944+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/hdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        3142    25238083+  83  Linux
/dev/hdb2            3143        3227      682762+  82  Linux swap / Solaris
/dev/hdb3            3228        4865    13157235   83  Linux

---

### Post by shane2peru on 2006-12-28
Ok, from the error, the uid number it looks as though your /dev/hda7 is problematic.  After looking at your outputs, in your fstab you have hda7 being mounted as a media type partition.  However in the fdisk it is listed as a linux-swap.   That isn't good.  That can cause some serious issues as you have discovered.  It appears as though you have another Linux system on there?  I see you also have a Windows installation on there.  What is hda7 supposed to be?  I'm assuming that it should be swap, since I don't see any other swap listed.  If it is supposed to be swap, then you need to comment out this line > # /dev/hda7
UUID=8e03b8f6-a08d-4634-93ee-3a8105a3183e /media/hda7 ext2 defaults 0 2 in your fstab by adding a # in front of the uuid part.  That should help.  You also didn't explain what you changed in your grub, that may have caused this.  May need more info if we want to figure the cause. ;) 

Shane

Oh, to edit your fstab you will need to put this in a terminal```
sudo gedit /etc/fstab
```  Be careful in editing your fstab.  Just comment out that line and reboot to see if that fixes it, if you aren't expecting that as a data partition.

---

### Post by sheine on 2006-12-28
Thank you Shane. You solved my problem. In retrospect, I mixed up a swap parition on 7 with a linux partition on 6.

---

### Post by shane2peru on 2006-12-29
No problem, glad to be of help!

Shane

---

### Post by NZ-Wanderer on 2007-01-07
I just had exactly the same error occur on my system after I had backed up my /home partition to another partition (I like keeping a backup of it) hda5 is where I copied it to, and hda5 is the one that gave the error..

I read in another thread that if you actually change the UUID to what the system thinks it is it works fine.

I did a 

```
ls /dev/disk/by-uuid/ alh
```

which gave me the current UUID values for my partitions, and then I just loaded fstab into an editor and edited the UUID of hda5 with the value I got in the command above.

Rebooting the system and I got no errors at all...

---

