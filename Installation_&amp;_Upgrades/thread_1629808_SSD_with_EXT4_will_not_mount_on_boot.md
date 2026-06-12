---
title: "SSD with EXT4 will not mount on boot"
date: 2010-11-24
forum: Installation &amp; Upgrades
---

### Post by objet petit a on 2010-11-24
Hello everybody, as a result of the help I got in [this topic](http://ubuntuforums.org/showthread.php?t=1627580), I am now closer to what I want than before, but there is still one thing. When booting I get the following error message:

```

The disk drive for EXT4 is not ready yet or not present.

Continue to wait; or press S to skip mounting or M for manual recovery.

```The drive in question is SSD2, which I wanted to mount as an extended disk (non OS). This is what I did:

**FDISK:**
```

Disk /dev/sdb: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00029baa

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7783    62516916   85  Linux extended

```**BLKID:**
```

/dev/sdb1: LABEL="SSD2" UUID="#######" TYPE="ext4"

```**FSTAB:**
```

UUID=####### ext4 /media/mountSSD2 defaults 0 2

```What is the problem? 
And what should I do?

---

### Post by objet petit a on 2010-11-24
*bumps*

---

### Post by efflandt on 2010-11-24
Why did you create an "extended" partition on /dev/sdb?  It looks like you have no logical or primary partition on that drive, therefore, no or misinterpreted content.  Why not simply create a "primary" partition if that is going to be its only partition?

---

### Post by itang sanjana on 2010-11-24
Here is the line of fstab in my machine
<file system> <mount point> <type> <options> <dump> <pass>

I see your
<file system> [COLOR="Red"]<type> <mount point>[/COLOR] <options> <dump> <pass>

What do you think?

---

### Post by objet petit a on 2010-11-25
Thanks for the tips people. I added a link to the original topic (which can be found [here](http://ubuntuforums.org/showthread.php?t=1627580) btw) in my opening post so you can see why I id what I did. 

More directly:
1) Does a second disk need a primary partition? I thought the term was used for the disc that would have an OS on it?
2) Will check the fstab.

---

### Post by sikander3786 on 2010-11-25
> 1) Does a second disk need a primary partition? I thought the term was used for the disc that would have an OS on it?

That isn't related to the OS in any way. At least one primary partition is recommended on every disc. You can have a maximum of 4 primary partitions. That can be by-passed by converting discs to dynamic or using LVM.

But the question here is that you need to create a primary partition.

And might also be something wrong in fstab as well.

Please post the output of these commands.

```
cat /etc/fstab
```

```
sudo blkid
```

Make sure your SSD is plugged in when you do those commands.

---

### Post by objet petit a on 2010-11-25
Okay, now I get a different, but almost identical error message:
```

The disk drive for /media/mountSSD2 is not ready yet or not present.

Continue to wait; or press S to skip mounting or M for manual recovery.
```


It seems to point to a problem with the kind of format I did. Perhaps indeed the fact that I made it only an extended partition?

---

### Post by sikander3786 on 2010-11-25
> The disk drive for /media/mountSSD2 is not ready yet or not present.

Continue to wait; or press S to skip mounting or M for manual recovery.

That means that there is something wrong in fstab. Please post the output of above mentioned commands.

---

### Post by Elfy on 2010-11-25
Without looking at the other thread I would wonder why you only have an extended - if you need to use that disk trying putting a logical inside the extended. 

You'll need the uuid for it after you have created it.

PS - I've never had an issue with a disk with only 1 extended and a lot of logicals

---

### Post by objet petit a on 2010-11-25
Okay, I&#314;l stop fiddling with it myself and just give you the requested output:

**BLKID**
```

/dev/sda1: UUID="#######" TYPE="ext4" 
/dev/sda5: UUID="#######" TYPE="swap" 
/dev/sdb1: LABEL="SSD2" UUID="#######" TYPE="ext4" 
/dev/sdc1: LABEL="DATA" UUID="#######" TYPE="ntfs" 

```

**FSTAB**
```

# / was on /dev/sda1 during installation
UUID=####### /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=####### none            swap    sw              0       0
UUID=####### ext4        /media/mountSSD2 defaults 0 2 
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

What can we learn from this?

---

### Post by sikander3786 on 2010-11-25
> UUID=####### ext4        /media/mountSSD2 defaults 0 2 


It needs to look like this.

```
UUID=####### /media/mountSSD2 ext4 defaults 0 2 

```

And make sure UUIDs match. That was no personal information that you were inclined to hide :P

Keeping **forestpiskie's** advice in mind, I hope you already have a logical partition in your extended one.

---

### Post by Elfy on 2010-11-25
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        7783    62516916   85  Linux extended
```

> **efflandt said:**
> Why did you create an "extended" partition on /dev/sdb?  It looks like you have no logical or primary partition on that drive, therefore, no or misinterpreted content.  Why not simply create a "primary" partition if that is going to be its only partition?

> **sikander3786 said:**
> Keeping **forestpiskie's** advice in mind, I hope you already have a logical partition in your extended one.

If the OP has not created one - it would appear that there is still no logical.

Might be an idea to get a new fdisk output

sudo fdisk -l

---

### Post by objet petit a on 2010-11-27
Hello everybody, I did as all of you said. Basically I started over and formatted the disk anew, creating the advised partition. After that I asked for a new UUID with fdisk. Then I edited my fstab again, this time in the proper order and it works like a charm now. All that is left is deleting a little lost&found folder from one failed attempt. But I think I can do this in the terminal with sudo su.


So, thanks again everybody, you bailed me out again.

Case Closed.

---

### Post by Elfy on 2010-11-28
You won't need sudo su or anything else - the lost and found folder will reappear anyway - get's created by the system for fsck checks I believe

---

### Post by objet petit a on 2010-11-28
What is it's purpose?

---

### Post by Elfy on 2010-11-28
A couple of links should help

[http://ubuntuforums.org/showpost.php?p=1336623&postcount=2](http://ubuntuforums.org/showpost.php?p=1336623&postcount=2)
[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by objet petit a on 2010-11-28
Cool, thanks.
:)

---

