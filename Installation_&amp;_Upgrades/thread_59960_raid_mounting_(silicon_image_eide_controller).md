---
title: "raid mounting (silicon image eide controller)"
date: 2005-08-25
forum: Installation &amp; Upgrades
---

### Post by ekravche on 2005-08-25
Hello,

I'm getting the following error (see attached image) when I try to mount 2 raid drives attached to a silicon image eide controller.

However, when I run the lines below in the terminal everything works fine
sudo mount -t ext3 /dev/hdc1 /media/hdc1/ 
sudo mount -t vfat /dev/hde1 /media/windows

I've looked into these threads, but I'm still stuck.

[http://www.ubuntuforums.org/showthread.php?t=58122&highlight=raid+mounting](http://www.ubuntuforums.org/showthread.php?t=58122&highlight=raid+mounting)
[http://www.ubuntuforums.org/showthread.php?t=57722&highlight=raid+mounting](http://www.ubuntuforums.org/showthread.php?t=57722&highlight=raid+mounting)
[http://www.ubuntuforums.org/showthread.php?t=54333](http://www.ubuntuforums.org/showthread.php?t=54333)

Any help regarding this would be greatly valued.

Thank you in advance.

---

### Post by nad on 2005-08-26
Your mount commands do not indicate software raid. Is this a hardware raid device?

---

### Post by ekravche on 2005-08-26
[QUOTE=nad]Your mount commands do not indicate software raid. Is this a hardware raid device?[/QUOTE]

I forgot to mention that I try to mount those drives automatically during startup by adding mounting info to  /etc/fstab. **So it is the fstab mounting that fails for me**. Here is how fstab looks like for me.


<--------------------------------------------------------------- fstab begin ----------------------------------------->
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hdc1	/media/hdc1	ext3	defaults	0	1
/dev/hde1       /media/windows  vfat    iocharset=utf8,umask=000   0       0
<--------------------------------------------------------------- fstab end  ----------------------------------------->

---

### Post by nad on 2005-08-26
Try removing the file system check from /dev/hdc1.

If you have an ext3 file system here and the mount succeeds, something else is fundamentally wrong.

Take the advice and run e2fsck with an alternate superblock.

---

### Post by ekravche on 2005-08-26
[QUOTE=nad]Try removing the file system check from /dev/hdc1.

If you have an ext3 file system here and the mount succeeds, something else is fundamentally wrong.

Take the advice and run e2fsck with an alternate superblock.[/QUOTE]


How do i remove the file system check?


The thing is that the mounting works for me when I run it in a terminal like so.
sudo mount -t ext3 /dev/hdc1 /media/hdc1/
sudo mount -t vfat /dev/hde1 /media/windows

It is just the fstab mounting that fails. Also on the note regarding e2fsck, I don't want this utility to damage the data on my drive.

---

### Post by nad on 2005-08-26
Then remove the default mount option and use 'noauto' . You can always mount the drive automatically at login from your .bash_profile . You will not get the error message anymore if you remove the file system check.

As far as damaging the data on your drive, if fsck is complaing of a bad superblock, your file system may already be damaged or your drive failing.

---

### Post by ekravche on 2005-08-26
[QUOTE=nad]Then remove the default mount option and use 'noauto' . You can always mount the drive automatically at login from your .bash_profile . You will not get the error message anymore if you remove the file system check.

As far as damaging the data on your drive, if fsck is complaing of a bad superblock, your file system may already be damaged or your drive failing.[/QUOTE]

How do i remove the file system check?

Thanx in advance

---

### Post by nad on 2005-08-26
I'm sorry. You did ask that already.

Change the 1 to a 0 at the end of the mount line. Or just leave off both digits.

---

### Post by ekravche on 2005-08-26
[QUOTE=nad]I'm sorry. You did ask that already.

Change the 1 to a 0 at the end of the mount line. Or just leave off both digits.[/QUOTE]

I've chnaged the 1 to a 0 at the end and now I get the following error (see screen shot attachme):
           mount: special device /dev/hdc1 does not exist
           mount: special device /dev/hde1 does not exist

---

### Post by ekravche on 2005-08-26
I think  I know what the problem is. The OS tries to mount the drives before the raid drives get a chance to be initialized. Anyway to get around this?

---

### Post by nad on 2005-08-26
Read post #6

---

### Post by ekravche on 2005-08-27
[QUOTE=nad]post #6 Then remove the default mount option and use 'noauto' . You can always mount the drive automatically at login from your .bash_profile . You will not get the error message anymore if you remove the file system check.

As far as damaging the data on your drive, if fsck is complaing of a bad superblock, your file system may already be damaged or your drive failing.[/QUOTE]

[QUOTE=nad]Read post #6[/QUOTE]

The only problem is that I have an admin user and a regular user. The regular user has no privilages. I always log on as a regular user for security purposes. So that when I try to mount from my regular user's .bash_profile it fails, because that user has limited privilages (again for security reason).

So how can I mount the drives connected to the raid controller via /etc/fstab?

Thank you in advance

---

### Post by ekravche on 2005-08-28
**RESOLUTION**
After reading many threads, here is how I resolved this problem.

I've created a new file /etc/rcS.d/**S50**mountraid. In this file I've placed the raid drives mount initialization calls below

mount -w -t vfat /dev/hdf1 /media/windows 
mount -w -t ext3 /dev/hdc /media/hdc

you also have to chmod a+xrw /etc/rcS.d/S50mountraid so that it's accessible to all users.

Notice that S50mountraid will be loaded after /etc/rcS.d/S40hotplug, and from what I've been reading S40hotplug loads the raid and scisi drivers. Thus, the reason why many people are having difficulties mounting their raid drives is because S35mountall.sh is called before S40hotplug. That is why many people are getting the device not found error when they try to load the raid drives in fstab.

**GOOD READS**
[http://www.ubuntuforums.org/showthread.php?t=2830](http://www.ubuntuforums.org/showthread.php?t=2830)
[http://www.ubuntuforums.org/showthread.php?t=28913](http://www.ubuntuforums.org/showthread.php?t=28913)
[http://www.ubuntuforums.org/showthread.php?t=57722](http://www.ubuntuforums.org/showthread.php?t=57722)

---

