---
title: "xfs not mounting correctly at boot."
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by iitywygms on 2009-09-28
Recently tried Karmic alpha 6.  I am running it on a mythbuntu backend."i know this is not smart"
I have 2 drives in the system.  I have the second drive as xfs mounting at /D2 which is a directory.
Sometimes when I boot, the computer just hangs.  Next time I boot, it will give and error message that it could not mount /D2, but the system will boot.
Now the strange thing is if I go into gparted and choose to unmount that drive (xfs) it will mount it, then every folder shows up as it should.

I need to get this fixed if possible.  Please let me know what info I can provide to help correct this.

here is fstab 

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=a06a4b59-c4e6-4042-a646-ac82106ad5a0 /               ext3    errors=remount-ro 0       1
# /var/lib was on /dev/sda6 during installation
UUID=31207765-d595-4ca7-a348-084dd3b531a5 /var/lib        xfs     defaults        0       2
# swap was on /dev/sda5 during installation
UUID=b2cfd117-3b2e-476d-a211-859d1a0454d1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1       /D2                                       xfs     defaults        0       0

---

### Post by iitywygms on 2009-09-29
bump

---

### Post by dabl on 2009-09-29
:confused:

You say:

> **iitywygms said:**
> Recently tried Karmic alpha 6.  I am  I have the second drive as xfs mounting at /D2 which is a directory.


But /etc/fstab says

> UUID=31207765-d595-4ca7-a348-084dd3b531a5 [COLOR="Red"]/var/lib[/COLOR] xfs defaults 0 2

/var/lib does not strike me as a sensible place to mount a drive/partition.  Why not make a mount point at, say /mnt/D2, and then edit /etc/fstab to match:


> UUID=31207765-d595-4ca7-a348-084dd3b531a5 [COLOR="Red"]/mnt/D2[/COLOR] xfs defaults 0 2

---

### Post by iitywygms on 2009-09-29
> **dabl said:**
> :confused:

You say:



But /etc/fstab says



/var/lib does not strike me as a sensible place to mount a drive/partition.  Why not make a mount point at, say /mnt/D2, and then edit /etc/fstab to match:

the /var/lib mount point was created by the default mythbuntu install.  I had nothing to do with that one.

I should be more clear.
I have 2 drives.

sda1 has a swap, ext3 for main operating system, xfs for video storage.
sda1 was created like this, by mythbuntu during the default install process.

sdb1 is the second drive, formatted as xfs, with the mount point of /D2

I added sdb1 about a year ago.  The above configuration worked fine with 9.04
Since the latest update to 9.10 alpha6, this drive (SDB1) has not been automounting at boot up.

This is the line that refers to sdb1 drive in fstab

/dev/sdb1 /D2 xfs defaults 0 0

---

### Post by dabl on 2009-09-29
> **iitywygms said:**
> 

This is the line that refers to sdb1 drive in fstab

/dev/sdb1 /D2 xfs defaults 0 0

Aha -- OK, got it.

Well, hmmmmmmmmmmmm.  I did notice on my system (3 drives, ~10 partitions, 3 filesystem types) that this new "fast boot" missed mounting two partitions yesterday.  I suspect it is flying through the partition-detecting and mounting process and missing things.  Hopefully the devs are testing and tuning it -- I wouldn't want to think that we're doomed to less than 100% auto-mounting of the filesystems listed in /etc/fstab.

I don't have any better suggestions for you. Personally, I'd change the mounting scheme for that second hard drive as I mentioned above, but perhaps it's more a matter of taste than rigour.  :-|

---

### Post by Anubis on 2009-09-30
I have the exact same issue. My partition is XFS in a LVM group. I have to run mount -a in a term to mount my XFS partitions. I used a double entry for one partition in fstab as a fix/workaround. That made the partition available. Seems like it does not have enough time to mount the partitions. has anyone filed a bug for this yet?

---

### Post by iitywygms on 2009-09-30
I have not filed a bug report.
When you do the double entry, did you use uuid or the old way?

---

### Post by iitywygms on 2009-10-01
I am running grub legacy.  Are any of you running grub2?  I wonder if upgrading to grub 2 would fix this?

---

### Post by Anubis on 2009-10-02
> **iitywygms said:**
> I have not filed a bug report.
When you do the double entry, did you use uuid or the old way?

I used the UUID way. I have Grub2 installed.):P

---

### Post by dino99 on 2009-10-02
> **iitywygms said:**
> I am running grub legacy.  Are any of you running grub2?  I wonder if upgrading to grub 2 would fix this?

grub2 is the default scheme now: so, as it is an dist-upgrade, you have to install os-prober & grub-pc; 

sudo aptitude install os-prober
sudo aptitude install grub-pc
sudo os-prober
sudo update-grub
sudo grub-mkconfig

test & if you agree then only use grub2.

---

### Post by Anubis on 2009-10-02
[https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/432620](https://bugs.launchpad.net/ubuntu/karmic/+source/mountall/+bug/432620)

Please lets focus on this bug report so this can get fixed?

---

### Post by Lepy on 2009-10-03
I'm glad that this is a bug and not user error on my part. I'm using UUID and grub.

I have 2 xfs partitions on my myth machine and one would always fail to mount, resulting in recordings not being found. Also, one of the partitions would mount as read only after a sudo mount -a. A few scheduled shows failed to record until I realized what was going on.

Hope this is fixed soon!

---

