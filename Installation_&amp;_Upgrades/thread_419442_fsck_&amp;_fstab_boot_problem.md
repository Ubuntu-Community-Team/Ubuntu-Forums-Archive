---
title: "fsck &amp; fstab boot problem"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by nereid on 2007-04-23
Hi folks,

after the update to Feisty and the change in the fstab to use UUIDs instead of the old fashioned method to address the harddrives my PC stops at every boot after an error with fsck. This gets me to the recovery console in which I have to mount my boot partition and my home partition by hand, after that resuming boot isn't  a problem.

I first thought this would be the known bug of wrong UUIDs in the fstab, but after issuing the following command  as root, they seem to be correct (issued for each partition)

```

cat /etc/fstab | grep `vol_id -u /dev/sda1`

```

My question now is this: How can I prevent fsck from bailing out and how can I get Ubuntu to boot without my help again.

Thanks in advance.

---

### Post by BoneKracker on 2007-04-23
The command you posted will simply retrieve selected contents of /etc/fstab.  So, if you were comparing the output of that command to your /etc/fstab, they definitely will match.  You probably know that and just didn't bother to post what you really compared the UUIDs listed in fstab against.   But just in case ...

...if you want to check what's in your fstab to verify that the correct UUID's were assigned, try using udev's vol_id utility (refer to "man vol_id").```
# /lib/udev/vol_id /dev/hda3 | grep UUID
ID_FS_UUID=5796fb0f-455b-47c9-9c8a-d637aa063e9e
```
(substituting the appropriate device name for "/dev/hda3" and repeating for each partition, naturally)

and/or this:```
# ls -l /dev/disk/by-uuid
```

Then you can compare those results to what has been entered into your /etc/fstab.

(I apologize if you did something similar and just didn't show it in your post.)

---

### Post by nereid on 2007-04-23
Thanks, sorry if my post wasn't clear. My snippet just shows, that the content of my fstab matches with my devices UUIDs, if it wouldn't, it would not print anything (I'm just too lazy to compare each UUID by hand or eye ;) ). So that this ain't my problem.

My problem is this, that fsck fails at every boot and I just don't like to manually mount each needed partition (in my case /boot and /home) so that I can continue to boot my system. I don't know but is there any log file to read which is created by fsck?

---

### Post by nereid on 2007-04-23
UPDATE:
I've found the fsck logfile

```

Log of fsck -C -R -A -a
Mon Apr 23 07:14:05 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: No such file or directory while trying to open /dev/.tmp-254-0
/dev/.tmp-254-0:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck.ext3: No such file or directory while trying to open /dev/.tmp-254-4
/dev/.tmp-254-4:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/mapper/sda5 has been mounted 70 times without being checked, check forced.
/dev/mapper/sda5: 1941/1221600 files (6.3% non-contiguous), 844730/2441368 blocks
/dev/mapper/sdb3: clean, 559/4889248 files, 7740937/9771536 blocks (check in 3 mounts)
fsck died with exit status 8

Mon Apr 23 07:14:23 2007
----------------


```

I just double checked the fstab and the mtab files and I couldn't find any partition called */dev/.tmp-254-0*. Is this something from udev? What does it do and for what is it needed?

---

### Post by BoneKracker on 2007-04-23
Sorry about that.

Yeah, that's what it looks like to me too.  I don't know what I'm talking about, but I think it could also be a problem within the init system or how it and udev are integrated to govern the boot-time fsck.

I didn't have this problem, but on my ubuntu box I'm using LVM on top of RAID, so I have mapper devices in there instead of UUIDs.  There are UUIDs for a couple of partitions that aren't within the logical volumes, but those seem to be working fine.  

I had to restrain my impulse to switch them back to readable device names.

If I were you, I'd consider backing up the fstab and then modifying it to use normal device names for now, until you sort it out.  You could check to see if there's a bug -- I have seen a lot of posts that seem to indicate this change has not been without issues.

---

### Post by nereid on 2007-04-23
You could be right that this could have to do something with the RAID. I don't use LVM or RAID and I even have uninstalled the mdadm RAID manager. Thanks for the suggestion and I think I will try for now to substitute the fstab UUIDs with the sdx names.

Beside this I would still like to know what these /dev/.tmp filesystems are about.

---

### Post by nereid on 2007-04-24
Now it confuses me totally. Just some minutes ago I booted my system and *drum roll* it booted without my help. I didn't change anything in the fstab or any other file concerning the filesystem. This makes me think about another OS, which is also very confusing in its way and where every new boot isn't the same as the last one ;)

---

### Post by BoneKracker on 2007-04-24
Had you applied any updates?  Maybe it _was_ a bug and it was fixed?

---

### Post by nereid on 2007-04-24
No, I did update amarok and kaffeine from the medibuntu repository but this hasn't anything to do with the filesystem.

And even the fsck log says that there isn't anything wrong. The mysterious /dev/.tmp filesystem has also vanished.

---

### Post by BoneKracker on 2007-04-24
That's funny.  Maybe udev has self-adaptive or learning tools.  

Well, glad it seems to be working out, especially since I didn't know how to help!
:)

---

### Post by nereid on 2007-04-24
Thanks anyway. I'm just surprised as you are, that this thing is booting without a hitch again. I'm just a little baffled...

---

### Post by double_v on 2007-05-24
Strange, I still have the same problem on my laptop. Sometimes the boot is smooth but other times it gets interrupted by fsck complaining that he is unable to find /dev/.tmp-* etc.

UUIDs are not a problem because I was successfully using them in edgy.

BTW, if WIP in "fsck 1.40-WIP" stands for Work In Progress, that's scary... :)

---

