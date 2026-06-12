---
title: "No writeaccess after reinstall hdd."
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by Azyx on 2010-11-04
I deleted and created a new partition. that appeare a new uuid on the drive and then i created an ext4 instead of ext3. now i have no write-access to the disk. How do I fix write access?

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=99ccc40a-7ba5-4d52-8669-8cd67b9d6cca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fb5a272a-f3bb-4a24-b8fa-d3980b082586 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=a4d7e909-dfea-44ee-8170-ae0d864c0732 none            swap    sw              0       0
#ATA-kortets diskar
UUID=b19f189b-7c89-45ff-b52b-c637df5a086e       /home/azyx/Hemma/280GB-E        ext4        relatime        0       2
#Old UUID=1c7a4002-4a38-4e0d-9c1c-1b047ccb156c       /home/azyx/Hemma/280GB-E        ext3        relatime        0      $
# /dev/sde1
UUID=a598b288-df32-4404-8348-a47aa0fcd150       /home/azyx/Hemma/280GB-D        reiserfs        relatime        0       2
# /dev/sdd1
UUID=feb51e21-b316-4f18-b1d1-d161c3a646f7       /home/azyx/Hemma/280GB-C        reiserfs        relatime        0       2
# /dev/sdc1
UUID=a1d838c2-5b99-495e-a97e-bb63392f1978       /home/azyx/Hemma/100GB-F        ext3        relatime        0       2
# /dev/sdf1
```

/cheers

---

### Post by dabl on 2010-11-04
Rather than give users direct access to the device, usually it's better to make a directory (a "folder") and give the user rw permissions in that.  It looks like you already have "280GB-E", so in a terminal you could

sudo chown joe:joe /home/azyx/Hemma/280GB-E

to change the permissions (and owner) of that directory to "joe", assuming "joe" is the name of the user that you want to have the access.

---

### Post by Azyx on 2010-11-04
> **dabl said:**
> Rather than give users direct access to the device, usually it's better to make a directory (a "folder") and give the user rw permissions in that.  It looks like you already have "280GB-E", so in a terminal you could

sudo chown joe:joe /home/azyx/Hemma/280GB-E

to change the permissions (and owner) of that directory to "joe", assuming "joe" is the name of the user that you want to have the access.

Ok. thanx. but there is something strange. look here:

```
azyx@Datorn:~$ cd Hemma
azyx@Datorn:~/Hemma$ ls -all
total 29
drwxr-xr-x  7 azyx azyx 4096 2010-07-28 14:05 .
drwxr-xr-x 38 azyx azyx 4096 2010-11-04 12:54 ..
drwxr-xr-x 10 azyx azyx 4096 2010-11-04 10:48 100GB-F
drwxrwxrwx 14 root root  856 2010-10-23 17:25 280GB-C
drwxrwxrwx  8 root root  296 2010-10-27 16:03 280GB-D
drwxr-xr-x  3 root root 4096 2010-11-04 11:44 280GB-E
drwx------  5 azyx azyx 4096 2010-07-01 13:49 .Trash-1000
azyx@Datorn:~/Hemma$ 
```

280GB_C work, even if root own it...

---

### Post by Azyx on 2010-11-04
> **dabl said:**
> Rather than give users direct access to the device, usually it's better to make a directory (a "folder") and give the user rw permissions in that.  It looks like you already have "280GB-E", so in a terminal you could

sudo chown joe:joe /home/azyx/Hemma/280GB-E

to change the permissions (and owner) of that directory to "joe", assuming "joe" is the name of the user that you want to have the access.

It says cannt create direktory then i try to create a folder  "Read-only file system".

---

### Post by dabl on 2010-11-04
You should not need to create a new directory, since you already have /home/azyx/Hemma/280GB-E.  Did you try the chown command that I wrote for you?

Having subdirectories owned by root, within your user's home directory, is not a good idea, by the way -- you may find your user's ability to log in to your home folder corrupted one of these days by root use of the subdirectories.  Here's a better structure, especially for hard drive partitions on your local computer:

You already have the /mnt directory in the root filesystem.  That's a great place to mount additional hard drive partitions.

So, you could ```
sudo mkdir -p /mnt/280GB-E
```

(and the same for those other partitions)

Then in /etc/fstab your mount line would be:

```
UUID=b19f189b-7c89-45ff-b52b-c637df5a086e    /mnt/280GB-E        ext4        relatime        0       2
```

Then, make a folder for whatever your data on that partition is:

```
sudo mkdir -p /mnt/280GB-E/MUSIC
```

for example, and then

```
sudo chown joe:joe /mnt/280GB-E/MUSIC
```

That way, root owns the partition, and joe own the folder and everything in it.

---

### Post by Azyx on 2010-11-05
> **dabl said:**
> You should not need to create a new directory, since you already have /home/azyx/Hemma/280GB-E.  Did you try the chown command that I wrote for you?

Yes, and the computer says: "Read-only file system", not that I don't have permission to to write.

Having subdirectories owned by root, within your user's home directory, is not a good idea, by the way -- you may find your user's ability to log in to your home folder corrupted one of these days by root use of the subdirectories.  Here's a better structure, especially for hard drive partitions on your local computer:

You already have the /mnt directory in the root filesystem.  That's a great place to mount additional hard drive partitions.

So, you could ```
sudo mkdir -p /mnt/280GB-E
```(and the same for those other partitions)

Then in /etc/fstab your mount line would be:

```
UUID=b19f189b-7c89-45ff-b52b-c637df5a086e    /mnt/280GB-E        ext4        relatime        0       2
```Then, make a folder for whatever your data on that partition is:

```
sudo mkdir -p /mnt/280GB-E/MUSIC
```for example, and then

```
sudo chown joe:joe /mnt/280GB-E/MUSIC
```That way, root owns the partition, and joe own the folder and everything in it.

Ok. Will try it later on. How do I access MUSIC from desktop? 

Now the 4 HDD appear on on the desktop as 3 '300 GB file system' and 1 '120 GB file system' and I don't know if it'a C, D or E. But I can not see them in the folder Desktop. I think I mount them in /home/azyx/Hemma to avoid them appear on the desktop (as Harddisk), but after I upgraded to Hardy(8.04), the still appear on the desktop (but not in the folder Desktop).

Cheers

---

### Post by dabl on 2010-11-05
I think there's a little confusion with the terminology.

You don't really mount a "drive", you mount a "partition".  Of course, it is possible that a drive could have only one partition.  So, for your system, "280GB-E" is a partition.  "MUSIC" is a directory that we made on that partition.  So you (root, or "sudo") mount the partition, and then you give the user a directory "MUSIC" that he can use for storing data.

"C", "D", and "E" have no meaning for Linux systems -- that is MS-DOS terminology.

As far as whether folders appear on your desktop, that is a Gnome setup that you can control.  If you don't want a folder on your desktop, just delete it, and then you can use Nautilus to find it.

---

### Post by Azyx on 2010-11-05
> **dabl said:**
> I think there's a little confusion with the terminology.

You don't really mount a "drive", you mount a "partition".  Of course, it is possible that a drive could have only one partition.  So, for your system, "280GB-E" is a partition.  "MUSIC" is a directory that we made on that partition.  So you (root, or "sudo") mount the partition, and then you give the user a directory "MUSIC" that he can use for storing data.

"C", "D", and "E" have no meaning for Linux systems -- that is MS-DOS terminology.

As far as whether folders appear on your desktop, that is a Gnome setup that you can control.  If you don't want a folder on your desktop, just delete it, and then you can use Nautilus to find it.

I just wrote C, D E instead of 280GB_C.... maybe i call them that was becaurse I use windows before a swift to ubuntu...or maybe it was becaurse of hdc, hdd and so they where called at that time 2005? 

I can not delete the pictures of harddisk, named '300 GB filesystem' on the gnome-desktop, I'm not root on the desktop. Maybe there are a gnomeconfigprogram somewere?

By the way, I should probably still have the disk mounted in /mnt or maybe it was /media? I don't rememer now. But now when they beguinne to popup on the desktop I can try to mount them in /mnt again... As I say, I will try that again, soon..

---

### Post by dabl on 2010-11-06
Your partition names are OK, if they mean something to you.  As I showed, you can mount them with the names that they have.

/media is used by the system for mounting removable devices.  You could also mount hard drive partitions there -- it doesn't hurt anything.  But /mnt is really for hard drive partitions.

---

### Post by Azyx on 2010-11-10
Thanx dabl, for all help, but I only get a read-only file system on 280GB-E :( After get a new UUID and some other things I make some changes in fstab like this:


```
# /etc/fstab: static file system information.
#
# Use 'sudo blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda3 during installation
UUID=99ccc40a-7ba5-4d52-8669-8cd67b9d6cca /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=fb5a272a-f3bb-4a24-b8fa-d3980b082586 /home           ext4    defaults        0       2
# swap was on /dev/sda1 during installation
UUID=a4d7e909-dfea-44ee-8170-ae0d864c0732 none            swap    sw              0       0
#ATA-kortets diskar
UUID=a598b288-df32-4404-8348-a47aa0fcd150       /home/Azyx/Hemma/280GB-D        reiserfs        relatime        0       2
UUID=feb51e21-b316-4f18-b1d1-d161c3a646f7       /home/Azyx/Hemma/280GB-C        reiserfs        relatime        0       2
UUID=a1d838c2-5b99-495e-a97e-bb63392f1978       /home/Azyx/Hemma/100GB-F        ext3        relatime        0       2
UUID=41def074-6b42-448f-b626-65e4ba4ee60c       /mnt/280GB-E        ext4        relatime        0       2
```But then when I try to make a directory in /mnt/280GB-E, I get this error:

```
Azyx@DasBlack:~$ sudo mkdir -p /mnt/280GB-E/MUSIC
mkdir: cannot create directory `/mnt/280GB-E/MUSIC': Read-only file system
Azyx@DasBlack:~$ 
```/Cheers




PS. Get new UUID after: Azyx@DasBlack:~$sudo blkid -o list -s UUID
device                   fs_type    label       mount point                  UUID
-----------------------------------------------------------------------------------------------------------------
/dev/sda1                ext3       100GB-F     /home/j0n1/Hemma/100GB-F     a1d838c2-5b99-495e-a97e-bb63392f1978
/dev/sdb1                ext4       280GB-E     /mnt/280GB-E                 41def074-6b42-448f-b626-65e4ba4ee60c
/dev/sdc1                reiserfs               /home/j0n1/Hemma/280GB-C     feb51e21-b316-4f18-b1d1-d161c3a646f7
/dev/sde1                swap                   <swap>                       a4d7e909-dfea-44ee-8170-ae0d864c0732
/dev/sde2                ext4                   /home                        fb5a272a-f3bb-4a24-b8fa-d3980b082586
/dev/sde3                ext4                   /                            99ccc40a-7ba5-4d52-8669-8cd67b9d6cca
/dev/sdd1                reiserfs               /home/j0n1/Hemma/280GB-D     a598b288-df32-4404-8348-a47aa0fcd150
/dev/sdf1                vfat       FREECOM HDD /media/FREECOM HDD           120D-2929
Azyx@DasBlack:~$

---

### Post by Azyx on 2010-11-10
It doesen't work. I could sudo mkdir -p /mnt/280GB-E/MUSIC, but when i try to sudo chown Azyx:Azyx /mnt/280GB-E/MUSIC, It say read-only file system. :(

---

### Post by Azyx on 2010-11-10
I find this in /var/syslog/  it was under the time I made a mkdir

```
Nov 10 23:02:58 DasBlack kernel: [  601.493646] EXT4-fs error (device sdb1): ext4_journal_start_sb: Detected aborted journal
Nov 10 23:02:58 DasBlack kernel: [  601.493661] EXT4-fs (sdb1): Remounting filesystem read-only
```As I understand it so unmount ubuntu the file system by some reason an mount it in read-only. but the reason is unknown. there are some bugg, that do the same thing, but it nay also be an error in the disk or the ata-card. I had problem with the ATA-card ( IT/ITE8212), then I upgradet from 6.06 to 8.04, and have to downgraded again, cos ubuntu had an unstable driver, and to get around it by adding the old kernel module or something. but after a year or so the fix the bug.

---

