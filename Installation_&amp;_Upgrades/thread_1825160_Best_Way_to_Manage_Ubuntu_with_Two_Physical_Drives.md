---
title: "Best Way to Manage Ubuntu with Two Physical Drives"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by SunsetSam on 2011-08-14
I am a long-time Windows and have just moved to a solely Ubuntu environment. 

I wondered if I may some advice on a recommended configuration for a desktop with two physical hard drives (SATA) with Ubuntu 11.04 installed.  Currently I have Ubuntu solely installed on one drive (Let me call it drive A), formatted EXT4 of course.  I previously had Windows 7 installed on this drive but did a reformat when installing Ubuntu.  The second drive (drive B) is what I would call a "data" drive. It has my photos, music, etc. on it and is formatted NTFS.  I want to keep my data on this drive in an OS-neutral manner.  That is, I would like to access it, not matter what OS I have on drive A.  Additionally  I want to be reformat/reinstall/replace Drive A as required,  without impacting Drive B and all my data.

So far so good.  Ubuntu sees Drive B OK and all its data.  However it seems I need to mount this drive first before I can use it.  That's isn't really a problem but some programs I use, e.g. Rhythmbox needs to have the drive mounted before it can play music located there.  All of which makes perfect sense and is clearly working as designed. I am just wondering if I have this figured out the best way.  My (limited) understanding is the Ubuntu could potentially see both disks as a single file system, rather than two physical disks. Indeed this is probably the way many would recommend. This approach would seem, to me, to limit my future options.  I would still prefer Drive B to be OS-neutral.

Any thoughts would be much appreciated. (And if this is the wrong place to post this, please let me know.)

---

### Post by varunendra on 2011-08-15
Hi, and welcome to the forums SunsetSam :)

You can add an entry in /etc/fstab file for any drive/partition to mount it automatically on startup. You can either mount it in an existing directory (like /home/<your userhome directory>) or create a new directory to mount in it. Syntax to add would be, as already depicted in the file:

**[COLOR=DarkRed]<file system>[/COLOR] [COLOR=Navy]<mount point>[/COLOR]   [COLOR=DarkRed]<type>[/COLOR]  [COLOR=Navy]<options>[/COLOR]       [COLOR=DarkRed]<dump>[/COLOR]  [COLOR=Navy]<pass>[/COLOR]**
For example:-
**[COLOR=DarkRed]/dev/sdb1[/COLOR] [COLOR=Navy]/media/storage[/COLOR] [COLOR=DarkRed]ntfs-3g[/COLOR][COLOR=Navy] defaults[/COLOR] [COLOR=DarkRed]0[/COLOR] [COLOR=Navy]0[/COLOR]**
where /dev/sdb1 is your 2nd drive's 1st partition, /media/storage is a newly created directory to use as a mount-point (with desired access permissions), ntfs-3g is the file-system type (ntfs-3g is used in linux to have both read/write permission on an ntfs filesystem), 'defaults' tells to use default mounting options, the first 0 (dump) tells the number after which the the filesystem should be backed up (0=ignore) and the last 0 decides the priority for fsck (0=ignore). You can have a look on details here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Having stated all of this, I'd say your current setup is perfectly ok given your future expectations, and doesn't need bothering with fstab. The only thing I'd prefer to put on a separate drive in your scenario is the swap partition, and even that only if your computer is too low on RAM and uses too much swapping of memory, which is very rare with modern systems.

Hope you enjoy these day-to-day linux games :)

---

### Post by fuzzyworbles on 2011-08-15
if you can, copy the stuff on your ntfs drive to your ext4 drive, format the ntfs drive to fat32, and move everything back. Then change the second zero in the fstab entry to 2. Doing so will enable you to perform file system checks on your data while still letting you use the drive under other operating systems. you can't fix ntfs file system corruption on linux.

---

### Post by varunendra on 2011-08-15
> **fuzzyworbles said:**
> if you can, copy the stuff on your ntfs drive to your ext4 drive, format the ntfs drive to fat32, and move everything back. Then change the second zero in the fstab entry to 2. Doing so will enable you to perform file system checks on your data while still letting you use the drive under other operating systems. you can't fix ntfs file system corruption on linux.
True! But I'd like to add that FAT32 has at least two very severe limitations:

[LIST=1]
[*]Larger block size - not suitable for large number of tiny files as it'll waste too much disk-space
[*]4 GB file size limit - won't allow creating more than 4GB sized file on the partition
[/LIST]
But if OP is comfortable with these limits, then FAT32 has definite advantage of availability of repairing option in his case as you suggested. Let's hear from him what are his priorities :)

---

### Post by SunsetSam on 2011-08-15
> **varunendra said:**
> Hi, and welcome to the forums SunsetSam :)

You can add an entry in /etc/fstab file for any drive/partition to mount it automatically on startup. You can either mount it in an existing directory (like /home/<your userhome directory>) or create a new directory to mount in it. Syntax to add would be, as already depicted in the file:

**[COLOR=DarkRed]<file system>[/COLOR] [COLOR=Navy]<mount point>[/COLOR]   [COLOR=DarkRed]<type>[/COLOR]  [COLOR=Navy]<options>[/COLOR]       [COLOR=DarkRed]<dump>[/COLOR]  [COLOR=Navy]<pass>[/COLOR]**
For example:-
**[COLOR=DarkRed]/dev/sdb1[/COLOR] [COLOR=Navy]/media/storage[/COLOR] [COLOR=DarkRed]ntfs-3g[/COLOR][COLOR=Navy] defaults[/COLOR] [COLOR=DarkRed]0[/COLOR] [COLOR=Navy]0[/COLOR]**
where /dev/sdb1 is your 2nd drive's 1st partition, /media/storage is a newly created directory to use as a mount-point (with desired access permissions), ntfs-3g is the file-system type (ntfs-3g is used in linux to have both read/write permission on an ntfs filesystem), 'defaults' tells to use default mounting options, the first 0 (dump) tells the number after which the the filesystem should be backed up (0=ignore) and the last 0 decides the priority for fsck (0=ignore). You can have a look on details here: [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

Having stated all of this, I'd say your current setup is perfectly ok given your future expectations, and doesn't need bothering with fstab. The only thing I'd prefer to put on a separate drive in your scenario is the swap partition, and even that only if your computer is too low on RAM and uses too much swapping of memory, which is very rare with modern systems.

Hope you enjoy these day-to-day linux games :)

**varunendra** - Thanks for this helpful suggestion and your welcoming comments. Both are very much appreciated.  I'll see about playing with fstab, but I am also reassured that my current setup is OK.  And I am enjoying the new Ubuntu experience too. Different certainly from over a decade with Windows, but glad that I have made the switch.

---

### Post by SunsetSam on 2011-08-15
> **fuzzyworbles said:**
> if you can, copy the stuff on your ntfs drive to your ext4 drive, format the ntfs drive to fat32, and move everything back. Then change the second zero in the fstab entry to 2. Doing so will enable you to perform file system checks on your data while still letting you use the drive under other operating systems. you can't fix ntfs file system corruption on linux.

**fuzzyworbles**. Thank you for your suggestion. My second drive is 2TB and so am wondering about the size factor here.  Disk Utility reports that this drive is in good health so am not so concerned with any file system corruption -well, not at this stage anyway!  Actually, Drive A has a few (7) bad sectors which I will need to keep an eye on to see if this worsens and I need to replace it. This has strengthened by desire to keep them separate.

---

### Post by SunsetSam on 2011-08-15
> **varunendra said:**
> True! But I'd like to add that FAT32 has at least two very severe limitations:

[LIST=1]
[*]Larger block size - not suitable for large number of tiny files as it'll waste too much disk-space
[*]4 GB file size limit - won't allow creating more than 4GB sized file on the partition
[/LIST]
But if OP is comfortable with these limits, then FAT32 has definite advantage of availability of repairing option in his case as you suggested. Let's hear from him what are his priorities :)
  
**varunendra** As noted in my earlier reply, the drive is 2TB and I may indeed have the odd file that is greater than 4GB. At this stage I'll probably stick with NTFS at this stage, but it is good to know I have another option should I need it.  And again, I appreciate the responses. As a newbie you always worry that you missing the obvious. And my experience with computers suggests that getting right in the beginning usually saves a whole heap of trouble further down the track. Especially with large drives.  I did a chkdsk on one of the drives under Windows, and gee, did that take a long time!

---

