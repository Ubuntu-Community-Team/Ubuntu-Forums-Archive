---
title: "Fresh install of 16.04.1 - Now mount problems"
date: 2016-10-18
forum: Installation &amp; Upgrades
---

### Post by oygle on 2016-10-18
Not sure if the mount problems are associated with these video problems - [https://ubuntuforums.org/showthread.php?t=2340444](https://ubuntuforums.org/showthread.php?t=2340444)

Since 16.04.1 fresh install, am unable to mount 2 hard drives. Here are the hard drives as shown by partition manager ..

dev/sda   500 Gb  (sda1 mounts as root, sda2 swap and sda3 mounts as /home )   mounts okay
dev/sdb   250 Gb  (sdb1 is windows xp - ntfs )   **[COLOR=#ff0000]FAILS[/COLOR]** to mount
dev/sdc   500 Gb  (sdc1  ext4 )   **[COLOR=#ff0000]FAILS[/COLOR]** to mount

The first 2 hard drives are internal; the 3rd hard drive is external. With 14.04, there was never a need to have an entry in /etc/fstab for dev/sdb

Now it seems 16.04.1 is getting stricter, because when I tried to mount the external, this is what was in the logs ..

> [   90.229414] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[  188.811980] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
[  331.353757] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem


So it seems that because there is no entry in /etc/fstab for dev/sdb , 16.04.1 assumes that it is 'ext4". Which it is not, it is "ntfs"  (Windows xp pro on it). Therefore, it seems that because of the failure to mount /dev/sdb , it can't mount the external drive, which is /dev/sdc

To try and trouble shoot this, I used "blkid". The result - nothing ??

Here is /etc/fstab 

> $ cat /etc/fstab                                                                                                                  
# /etc/fstab: static file system information.                                                                                                         
#                                                                                                                                                     
# Use 'blkid' to print the universally unique identifier for a                                                                                        
# device; this may be used with UUID= as a more robust way to name devices                                                                            
# that works even if disks are added and removed. See fstab(5).                                                                                       
#                                                                                                                                                     
# <file system> <mount point>   <type>  <options>       <dump>  <pass>                                                                                
# / was on /dev/sda1 during installation                                                                                                              
UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca /               ext4    errors=remount-ro 0       1                                                         
# /home was on /dev/sda3 during installation                                                                                                          
UUID=4925dcbd-b2a1-4db6-adc0-69a9f05ad473 /home           ext4    defaults        0       2                                                           
# swap was on /dev/sda2 during installation
UUID=82e48eb2-0c33-4696-9154-d921da42bbd2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# / external hard drive - 500Gb
UUID=8EFC2D0BFC2CEF61 /media/externaldisk               ext4    noauto,errors=remount-ro 0       1


So, can anyone direct me how to add an entry in /etc/fstab for /dev/sdb , and also how to create the mount point please. :)

---

### Post by semiscary on 2016-10-18
[SIZE=4]Why do you still have Windows XP?[/SIZE] o_O

---

### Post by oygle on 2016-10-18
> **semiscary said:**
> [SIZE=4]Why do you still have Windows XP?[/SIZE] o_O

I don't want to buy Windows 10 or similar. Would rather use Ubuntu. :)

But seriously, did your question help me with the mount problem ?  :D

---

### Post by oygle on 2016-10-18
Realised that I couldn't use "blkid needed sudo, despite the fact there was no msg about permissions ??

> $ sudo **blkid** 
[sudo] password for ********: 
/dev/sda1: UUID="855c6698-a72d-4cc5-8b7e-3dee0c8b7fca" TYPE="ext4" PARTUUID="0009cba2-01"
/dev/sda2: UUID="82e48eb2-0c33-4696-9154-d921da42bbd2" TYPE="swap" PARTUUID="0009cba2-02"
/dev/sda3: UUID="4925dcbd-b2a1-4db6-adc0-69a9f05ad473" TYPE="ext4" PARTUUID="0009cba2-03"
/dev/sdb1: UUID="8EFC2D0BFC2CEF61" TYPE="ntfs" PARTUUID="0b410b41-01"

and some more information on the first 2 hard drives, using **sudo fdisk -lu**

> 
Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009cba2

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *          63  41945714  41945652    20G 83 Linux
/dev/sda2       41945715  50347709   8401995     4G 82 Linux swap / Solaris
/dev/sda3       50347710 976768064 926420355 441.8G 83 Linux


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b410b41

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *       63 488375999 488375937 232.9G  7 HPFS/NTFS/exFAT


---

### Post by Bashing-om on 2016-10-18
oygle; Hey ...

Though I am no longer Windows literate, I will give this a push along.

here:
> 
To try and trouble shoot this, I used "blkid". The result - nothing ??

nothing is what the system is going to do in this instance, blkid can be very destructive if not used properly, the system protects it's self by making sure this is what you want to do .
try as:
```

sudo blkid

```
that you really want to see what is in that cache.
To clear cache and get new view:
```

sudo blkid -c /dev/null -o list

```

Now to the situation at hand to access partitions.

As you have not set up in fstab to "automount" them then the only means is via the GUI - presently.

Now we need to know that the targets do exist, and what the file systems are.
Post back - between code tags . the outputs of terminal commands:
```

sudo blkid -c /dev/null -o list
sudo fdisk -lu
ls -al /media/<username>/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
code tags to maintain formatting and to promote readability.

Let's see if we see what we expect the system to see.

[INDENT][INDENT]I thout I saw a puddy cat
[/INDENT][/INDENT]

---

### Post by oygle on 2016-10-18
> **Bashing-om said:**
> nothing is what the system is going to do in this instance, blkid can be very destructive if not used properly, the system protects it's self by making sure this is what you want to do .
try as:
```

sudo blkid

```

Yes, thanks. I had only just worked that one out.  :)

> **Bashing-om said:**
> Now we need to know that the targets do exist, and what the file systems are.
Post back - between code tags . the outputs of terminal commands:
```

sudo blkid -c /dev/null -o list
sudo fdisk -lu
ls -al /media/<username>/

```

Okay - here is the output ..

```
sudo blkid -c /dev/null -o list
```
> 
device                                 fs_type        label           mount point                                UUID
-----------------------------------------------------------------------------------------------------------------------------------------------------
/dev/sda1                              ext4                           /                                          855c6698-a72d-4cc5-8b7e-3dee0c8b7fca
/dev/sda2                              swap                           [SWAP]                                     82e48eb2-0c33-4696-9154-d921da42bbd2
/dev/sda3                              ext4                           /home                                      4925dcbd-b2a1-4db6-adc0-69a9f05ad473
/dev/sdb1                              ntfs                           (not mounted)                              8EFC2D0BFC2CEF61


```
sudo fdisk -lu
```
> Disk /dev/ram0: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram1: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes                                                                                                                 
Sector size (logical/physical): 512 bytes / 4096 bytes                                                                                                
I/O size (minimum/optimal): 4096 bytes / 4096 bytes                                                                                                   
                                                                                                                                                      
                                                                                                                                                      
Disk /dev/ram2: 64 MiB, 67108864 bytes, 131072 sectors                                                                                                
Units: sectors of 1 * 512 = 512 bytes                                                                                                                 
Sector size (logical/physical): 512 bytes / 4096 bytes                                                                                                
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram3: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram4: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram5: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram6: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram7: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram8: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram9: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram10: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram11: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram12: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram13: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram14: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/ram15: 64 MiB, 67108864 bytes, 131072 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0009cba2

Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *          63  41945714  41945652    20G 83 Linux
/dev/sda2       41945715  50347709   8401995     4G 82 Linux swap / Solaris
/dev/sda3       50347710 976768064 926420355 441.8G 83 Linux


Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0b410b41

Device     Boot Start       End   Sectors   Size Id Type
/dev/sdb1  *       63 488375999 488375937 232.9G  7 HPFS/NTFS/exFAT


```
ls -al /media/********/
```
> total 8
drwxr-x---+ 2 root root 4096 Oct 19 12:17 .
drwxr-xr-x  6 root root 4096 Oct 19 13:11 ..


I have also been working my way through ths - [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions). I haven't retrived the UUID of the external drive as yet, because the mounting process fails on that Windows HDD. Anyway, here is /etc/fstab now ..

> 
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=855c6698-a72d-4cc5-8b7e-3dee0c8b7fca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=4925dcbd-b2a1-4db6-adc0-69a9f05ad473 /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=82e48eb2-0c33-4696-9154-d921da42bbd2 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
# / Windows XP pro hard drive - 250 Gb
UUID=8EFC2D0BFC2CEF61  /media/Winxppro  ntfs-3g  defaults,windows_names,locale=en_AU.UTF-8  0 0
# / external hard drive - 500Gb
###UUID=8EFC2D0BFC2CEF61 /media/externaldisk               ext4    noauto,errors=remount-ro 0       1


---

### Post by Bashing-om on 2016-10-18
oygle; Ho Kay .. look'n good  ----

But !!

in fstab see this mount point 
> 
UUID=8EFC2D0BFC2CEF61 [color=red]/media/Winxppro[/color]

that does not exist !
per:
> 
ls -al /media/********/

total 8
drwxr-x---+ 2 root root 4096 Oct 19 12:17 .
drwxr-xr-x 6 root root 4096 Oct 19 13:11 ..


So next we make up that mount point
```

sudo mkdir /media/<username>/Winxppro

```
Keep on mind that linux (ubuntu) is case sensitive in that W does not equal w .

Make real sure that the system likes the present fstab:
```

sudo mount -a

```
if the return is back to prompt - no sas or backtalk .., system is happy with the fstab file.

now reboot and see if you have access to 
8EFC2D0BFC2CEF61 

```

ls -al /media/<username>/Winxppro

```

maybe yes 
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT]

---

### Post by oygle on 2016-10-21
> **Bashing-om said:**
> oygle; Ho Kay .. look'n good  ----

Thanks a lot for your help. Am now able to mount the Windows HDD and the external drive just fine.  :)

Also, since this mount problem is resolved, the [video/display problems]("https://ubuntuforums.org/showthread.php?t=2340444") have significantly diminished.

---

### Post by Bashing-om on 2016-10-21
oygle; Great !

We do good work !
Pleased ya got it all sorted out.

[INDENT][INDENT]'buntu
[INDENT][INDENT][INDENT]together we can
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by oygle on 2016-10-22
> **Bashing-om said:**
> 
Pleased ya got it all sorted out.

I'm pleased you helped. Thanks.  :)

---

