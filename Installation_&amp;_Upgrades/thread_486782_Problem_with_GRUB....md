---
title: "Problem with GRUB..."
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by angelinatoress on 2007-06-28
As the thread titles suggests, I am having a problem with GRUB.  I recieve an error message when GRUB is loading.  It starts as usual "GRUB loading stage 1.5" then immediately goes to "Error 2".  I did a search for "GRUB Error 2" and just "Error 2" in these forums but found nothing relevant.

This all started when I decided to format a 200GB WD2000 HDD that was in the format of NTFS as I previously used it as my media drive when I had Windows XP Professional on this system.  I got sick of having no ability to write to it.  So, I popped in my Ubuntu disc and rebooted the system and booted on to my CD/DVD-Rom.

I decided to format the entire hard drive and install Ubuntu on it 100%.  Everything seemed to go fine and dandy but when I rebooted it popped up with that "Error 2".  So I switched around the Master and slave drives to see if that would remedy the problem but to no avail.  After hours of frustration and reformatting, I decided to just sign up here and let someone with more expierence give me a hand.

My system specifications:

Ubuntu 7.04 Fiesty Fawn.
60 GB HDD.  (Had Fiesty running perfectly beforehand.)
200 GB HDD.  (Was running NTFS)
Core Duo processor.

Any help would be greatly appreciated.  Thank you.

---

### Post by logos34 on 2007-06-28
> I got sick of having no ability to write to it.

Well, actually you could have used the ntfs-3g driver, but no matter.

> I decided to format the entire hard drive and install Ubuntu on it 100%. Everything seemed to go fine and dandy but when I rebooted it popped up with that "Error 2". So I switched around the Master and slave drives to see if that would remedy the problem but to no avail. After hours of frustration and reformatting...
....

Ubuntu 7.04 Fiesty Fawn.
60 GB HDD. (Had Fiesty running perfectly beforehand.)
200 GB HDD. (Was running NTFS)

Error 2:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#2_](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#2_)

So are you using the live cd now or working from the previous install on the 60gb?

You might want to post the output of these two commands:

**sudo fdisk -l** (lower case L)
**cat /boot/grub/menu.lst**

---

### Post by dabl on 2007-06-28
If you're looking for a quick and easy solution, and don't need to access that hard drive from Windows any more, just use your Ubuntu live CD, run GParted, and repartition it (to one or multiple partitions, as you wish), and then format it as ext3 or reiserfs.  Then you can mount it under your Linux filesystem and life should be grand. :)

---

### Post by angelinatoress on 2007-06-28
Thanks for your help.

I was able to get everything working again.  Except 1 thing.  The 60gb drive.

It says in "Computer":  "55.9 GB Volume" but I have to mount it.  When I do it mounts it like normal.  But I can not read or write to it even though the drive is formatted in ext3.  The drive is under "Root" and I have no clue on how to reclaim it.  :(

Again, thanks for you help previously and anymore help would be greatly appreciated.

---

### Post by Pumalite on 2007-06-28
Sorry wrong post

---

### Post by confused57 on 2007-06-28
Here's an excellent guide for mounting an ext3 partition in fstab:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

---

### Post by logos34 on 2007-06-28
> **angelinatoress said:**
> ...It says in "Computer":  "55.9 GB Volume" but I have to mount it.  When I do it mounts it like normal.  But I can not read or write to it even though the drive is formatted in ext3.  The drive is under "Root" and I have no clue on how to reclaim it

Post you fstab.  But it may be a permissions issue like pumalite suggested. [ok he retracted that i see]
[B]
cat /etc/fstab[/B]

---

### Post by angelinatoress on 2007-06-28
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=d96c66e4-7c5e-4c64-903d-f4526e6606da /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=74f66aff-b908-4bde-b9e5-e4b311a3af07 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
```

There is my fstab.  Hope this helps?

---

### Post by logos34 on 2007-06-28
maybe it's something to do with the uuid or permissions.

what does 

**ls -l /dev/disk/by-uuid**

show?

---

### Post by logos34 on 2007-06-28
wait, you never posted your fdisk.  maybe its the fstab just for 200gb install  
[B]
sudo fdisk -l [/B]

---

### Post by angelinatoress on 2007-06-28
This is what fdisk shows:

```
angel@desktop:~$ sudo fdisk -l
Password:

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       23849   191567061   83  Linux
/dev/sda2           23850       24321     3791340    5  Extended
/dev/sda5           23850       24321     3791308+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7297    58613121   83  Linux
angel@desktop:~$ 

```

This is what ls does:

```
angel@desktop:~$ ls -l /dev/disk/by-uuid
total 0
lrwxrwxrwx 1 root root 10 2007-06-28 15:36 74f66aff-b908-4bde-b9e5-e4b311a3af07 -> ../../sda5
lrwxrwxrwx 1 root root 10 2007-06-28 15:36 79ae0dca-c2d4-4dbc-8f0b-0c8e6dcdefb0 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2007-06-28 15:36 d96c66e4-7c5e-4c64-903d-f4526e6606da -> ../../sda1
angel@desktop:~$ 

```

---

### Post by logos34 on 2007-06-28
Ok, so then it should be pretty easy.  Try this:

gksudo gedit /etc/fstab

You can add sbd1 to the bottom like this:

> # /dev/sdb1
UUID=79ae0dca-c2d4-4dbc-8f0b-0c8e6dcdefb0 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

Or

> /dev/sdb1 /media/sdb1 ext3 defaults,errors=remount-ro 0 1

then creat the mount point:

**sudo mkdir /media/sdb1**

(or maybe you already have a dir 'sdb1' in /media

Close all your apps and docs and restart the desktop,  Should automount.
[B]
ctrl+alt+backspace[/B]

---

### Post by angelinatoress on 2007-06-28
I now get this error:

[[IMG]http://img443.imageshack.us/img443/2489/snapshot1bv9.th.png[/IMG]](http://img443.imageshack.us/img443/2489/snapshot1bv9.png)

---

### Post by confused57 on 2007-06-28
Maybe this entry in fstab will work:
```
#/dev/sdb1       
UUID=79ae0dca-c2d4-4dbc-8f0b-0c8e6dcdefb0 /media/sdb1 ext3  rw,user  0    1
```

This is the format is from the link that I supplied earlier from Herman's website.

---

### Post by Pumalite on 2007-06-28
Where is the disk mounted? If it's let's say, /media/disk1, then try this ( see if it works, I'm not sure)

sudo chmod 777 /media/disk1 ( or whatever is suitable ).

---

### Post by logos34 on 2007-06-28
try reboot. 

basically we're just tellng it to automount with root/user permissions per fstab entry (that's the standard entry).  And
your permissions for that volume in the ls -l uuid command look exactly like mine.

edit: try confused57 entry.  Or just chmod the permissions for 'everyon' as in pumalite post

---

### Post by angelinatoress on 2007-06-29
Alright, it auto-mounts now.

I tried the chmod command and it pops up with this:

```
angel@desktop:~$ sudo chmod 777 /media/sdb1
bliss@desktop:~$ 

```
So it seems to allow it to go through, but it doesn't.  I still don't have any permissions.

I tried to unmount the volume, so I can see if it just needs remounting, but no go.  It pops up with:
> Cannot unmount the volume
Details:
umount: /media/sdb1 mount disagrees with the fstab

This is what I have setup as the fstab for it:
```
#/dev/sdb1       
UUID=79ae0dca-c2d4-4dbc-8f0b-0c8e6dcdefb0 /media/sdb1 ext3  rw,user  0    1
```

---

### Post by Pumalite on 2007-06-29
> **angelinatoress said:**
> Alright, it auto-mounts now.

I tried the chmod command and it pops up with this:

```
angel@desktop:~$ sudo chmod 777 /media/sdb1
bliss@desktop:~$ 

```
So it seems to allow it to go through, but it doesn't.  I still don't have any permissions.

I tried to unmount the volume, so I can see if it just needs remounting, but no go.  It pops up with:


This is what I have setup as the fstab for it:
```
#/dev/sdb1       
UUID=79ae0dca-c2d4-4dbc-8f0b-0c8e6dcdefb0 /media/sdb1 ext3  rw,user  0    1
```

Close all apps. Reboot. Try your drive first before applying permissions. Maybe all is needed is the line confused57 gave you for automount.

---

### Post by angelinatoress on 2007-06-29
Still no go on it after a reboot.  It is still saying that the owner is the root.

Edit:  I just tried the chmod, and it asked me for my password and still no go on allowing permissions.

---

### Post by Pumalite on 2007-06-29
Try: sudo su. After the password, navigate to the drive and see what you get.

---

### Post by confused57 on 2007-06-29
Maybe you need to change owner:
```
sudo chown -R angel:angel /media/sdb1
```

---

### Post by angelinatoress on 2007-06-29
I did this:

```
angel@desktop:~$ sudo su
Password:
root@desktop:/home/angel# nautilus /media/sdb1

(nautilus:13725): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
Initializing gnome-mount extension

```

Now I am able to access the "sdb1 Properties".  I click on "Permissions" and I am able to change owner and what not.  I am making it:

> Owner:  angel - Angelina
Folder Access:  Create and delete files
File Access: Read and write

Group:  angel
Folder Access:  Create and delete files
File Access:  Read and write

Others
Folder Access:  Create and delete files
File Access:  Read and write


Hopefully this will allow me to read and write to the hard drive.

I can't rename the drive, but this is dandy enough for me.  Hopefully I won't have to do it every time I reboot.

Edit:  It did indeed work.  :)  I just closed out the terminal based nautilus and closed out the terminal and double clicked on the drive on the desktop and I am able to create a folder and even drag and drop folders onto the drive.

Now time to figure out how to rename the drive.  Thank you all for your help in getting this back on track.  :)

---

