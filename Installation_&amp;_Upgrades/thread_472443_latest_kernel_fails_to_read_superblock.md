---
title: "latest kernel fails to read superblock"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by moshuptrail on 2007-06-13
I just took the latest set of updates and now Ubuntu won't boot.
I get an error something like:
fsck failed to find superblock, try e2fsck -b 8193 <dev>
This is with kernel 2.6.20-16-386

However, if I simply revert to an older kernel, the system boots fine.  The superblock is read fine:
This is with kernel 2.6.17-11-386

Is this a new feature?  :)

I'm a bit baffled.  Any suggestions?  Info needed?

---

### Post by bananabob on 2007-06-13
Me too! 
uname -r gives me

> 2.6.20-16-generic

Sometimes when I boot I get this message

> Log of fsck -C -R -A -a 
Thu Jun 14 10:17:08 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/Volume0/lvol0
/dev/Volume0/lvol0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Thu Jun 14 10:17:08 2007
----------------


The interesting thing is if I do a reboot it goes away! and I the system boots normally.
Also it doesn't happen all the time.

So what to do? How do you revert back to a working versionl? Has it been posted as a bug?

---

### Post by moshuptrail on 2007-06-13
To revert to a working version, I simply choose an older kernel at the grub menu.  It usually leaves you with 1 or 2 back.

I am getting the exact same message, but it's more consistent on my PC.

---

### Post by moshuptrail on 2007-06-20
In case anyone cares...
I think this problem is caused by the way my /etc/fstab file is written.
There are two partitions on my system that have duplicate UUIDs with two other partitions.  This prevented Edgy from upgrading my fstab to UUID designations.  Edgy and Feisty could both use the /dev/hdax notation until now.  With Feisty it's no longer supported!  By manually converting my fstab to UUID format I can now boot.

I've now got a separate post trying to figure out how to change the UUID on a NTFS or FAT32 partition - without frying it!

---

### Post by bananabob on 2007-06-20
Ovewr the last few days I have had no problems what so ever. Maybe it is fixed. I'll let you know if it isn't

---

### Post by moshuptrail on 2007-06-20
Is your fstab and menu.lst written with UUID designations now?

---

### Post by bananabob on 2007-06-20
Looks like the fstab is but the menu.lst isn't

---

### Post by bananabob on 2007-06-21
Oh well I spoke to soon

This morning it took me two attempts to get logged in.

Both times I was a victim of the bad superblock problem!

---

### Post by elektronaut on 2007-08-14
In case it's not a problem with inconsistent UUID's, it could also be a superfluous entry in fstab - like in my case for a LVM partition on an external drive that was not connected.

---

### Post by bananabob on 2007-08-14
I don't think that my problem is either of those.

And I still get it every so often.

---

