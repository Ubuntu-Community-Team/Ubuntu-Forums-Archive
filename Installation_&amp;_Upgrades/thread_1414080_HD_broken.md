---
title: "HD broken"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by joep-vd on 2010-02-23
I am trying to make some samba sharing work, and suddenly the /dev/sda5 partition refuses to get mounted. 

after ```
sudo mount -a
```, I get: 
```
wrong fs type, bad option, bad superblock on /dev/sda5 missing codepage or helper program, or other errorIn some cases useful info is found in syslog - try dmesg | tail  or so
```

I tried to fix the codeblock with testdisk, but the error message remains the same. 

and, finally my fstab: 

```

**fstab**
/dev/sda5 /media/movies ext2 rw,suid,dev,exec,auto,user,async,uid=1000 0 0
UUID=8234-D8BE /media/data vfat rw,suid,dev,exec,auto,user,async,uid=1000 0 0

```

and the first one is broken, the second one works perfectly fine... 

Any help would be appreciated... 

Cheers!

---

### Post by dabl on 2010-02-23
Have you tried an fsck on that partition lately?  That would be a good thing to do.

Assuming ```
sudo blkid
``` and ```
sudo fdisk -lu
``` confirm the /dev/sda5 filesystem type, there is nothing obviously wrong with your /etc/fstab file.  I personally prefer "mount-by-uuid" but that is not mandatory.

Since it is always possible that there really is some physical problem with that partition, the first thing to do is to boot a Live CD and back up your data (I'd back up everything on /dev/sda).

Then, with your data safe, you've got some choices.  If you want to play "disk detective", you can use something like [[COLOR="SeaGreen"]**Hiren's**[/COLOR]](http://www.hiren.info/pages/bootcd) and build your skills as a hdd recovery technician. Or, you can use GParted and remake/reformat that partition on the chance that it will be OK once it is reformatted.

---

### Post by joep-vd on 2010-02-23
I was already afraid of such an answer... fsck thinks all is fine, and all other tools also agree it's an ext2 partition. Guess I'll have to consider the partition dead... 

First I need to fix myself a large enough back-up disk :/ 

You have any clue as to how suddenly such a partition corruption could occur? I've been toying around with samba, and as such also with user permissions on this disk. But that cannot break a disk to this extent, can it? What else could have gone wrong?

---

### Post by dabl on 2010-02-23
Do you get the same error message when you do a manual mount like this:
```

sudo mount -t ext2 /dev/sda5 /media/movies
```

?

I assume /media/movies is a valid mount point, and not being used by any other device?

I would not think the error that you're getting would be due to a permissions issue.  FYI, root permission are normally automatically assigned to _devices_ and _mount points_ and my experience indicates it is best to leave it that way.  User permissions can be assigned to _directories_ that have been created for user data, if that is appropriate to manage your data.

So /dev/sda5 and /media/movies should have root permissions only, and /media/movies can have a folder owned by your user.

---

### Post by joep-vd on 2010-02-23
hell yeah! with this command the mount worked!?!?! 

```
sudo mount -t ext2 /dev/sda5 /media/movies
```

You have saved a day or two! 

And also reloading the fstab works with mount -a, and i don't get this alarming message. 

But if I first unmount the drive, then reload the fstab, then my install has lost it again. This manual mount is some magic trick... 

Double-check: Also this line in fstab doesn't work: 

```
/dev/sda5 /media/movies ext2 default 0 0
```

Any clue how this magic could be translated to the fstab config?

---

### Post by dabl on 2010-02-24
> **joep-vd said:**
> 

Double-check: Also this line in fstab doesn't work: 

```
/dev/sda5 /media/movies ext2 default 0 0
```

Any clue how this magic could be translated to the fstab config?

There are two unrelated problems here, I think.

The one that affects mounting is the "default" option.  The correct spelling is "default_s_".

The other one is the "0" pass option (the second 0).  This disables filesystem checking -- maybe you mean to do that, but it's not a wise choice if you care about your data.  Normal choice for non-root filesystems is "2".  So, I'm saying that line in /etc/fstab should be edited to read:
> 
 /dev/sda5 /media/movies ext2 defaults 0 2

---

### Post by joep-vd on 2010-02-24
Feel like an idiot now... Just assuming that the default setting would be called for by the singular noun. 

The setting 0 or 2 didn't make a difference. But I'll take your suggestion and use the checking. 

Thanks a bunch, dabl!

---

### Post by dabl on 2010-02-24
> **joep-vd said:**
> Feel like an idiot now... Just assuming that the default setting would be called for by the singular noun. 

The setting 0 or 2 didn't make a difference. But I'll take your suggestion and use the checking. 

Thanks a bunch, dabl!

You're welcome.

BTW, I would advise changing to ext3 or ext4 the next time you do anything with it.  Either one will provide a better chance of recovery should you lose power or otherwise have a crash.

---

