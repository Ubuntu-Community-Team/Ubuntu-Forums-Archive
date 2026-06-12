---
title: "Error on boot - after upgade - Mounting"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by myharries on 2010-04-30
**Error while Mounting /etc/fstab** 
I get the following error, after I upgraded, when i boot i get...
Error while mounting /etc/fstab
press s to skip or m for manual recovery.

Pressing s works, but next time I boot it hangs there again. Unfortunately I'm an absolute beginner with Ubuntu.
There was an error in the file at first, where sde1 was not mounted, and sda1 was mounted ( a second time) in sdb1 position.
Also please note, that the HDD's are not in a raid system, the name is a carry over from a previous setup

Could someone knowledgable give me some direction on how to stop this error? Thanks

-----------------------------------------------------------

/etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# / was on /dev/sda1 during installation
UUID=e3dcc4fd-9d63-471f-8933-f12fa66eafd4 / ext3 relatime,errors=remount-ro 0 1
# swap was on /dev/sda5 during installation
UUID=9b6ff94b-0251-45ac-a167-8e5cb19fc49b none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/sdb1 /var/raid01 ext3 defaults,errors=remount-ro 0 2
/dev/sdc1 /var/raid02 ext3 defaults,errors=remount-ro 0 2
/dev/sdd1 /var/raid03 ext3 defaults,errors=remount-ro 0 2
/dev/sde1 /var/raid04 ext3 defaults,errors=remount-ro 0 2

---

### Post by ram130 on 2010-05-01
same here..

> # /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=8e7cae7b-970b-4f7e-8d8c-410f3613877d /               ext4     relatime,errors=remount-ro 0       1
   sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by myharries on 2010-05-01
Just a bump as I need help..... sorry

---

### Post by myharries on 2010-05-02
Dont worry, someone ( nicolinux ) tipped me off to the problem,
 
For some reason when the upgrade created the new fstab file it left off the comment # at the beginning of the file
eg...
[COLOR=darkred]/etc/fstab: static file system information[/COLOR].
 
which should have been

[COLOR=darkred]#/etc/fstab: static file system information[/COLOR]
 
Thanks Nicolinux!!!!

---

### Post by ram130 on 2010-05-02
> **myharries said:**
> Dont worry, someone ( nicolinux ) tipped me off to the problem,
 
For some reason when the upgrade created the new fstab file it left off the comment # at the beginning of the file
eg...
[COLOR=darkred]/etc/fstab: static file system information[/COLOR].
 
which should have been

[COLOR=darkred]#/etc/fstab: static file system information[/COLOR]
 
Thanks Nicolinux!!!!

Yea I realise this too!! but didn't know how to explain it since I also removed my main drive that was mounting. All seems well again, just a  lil slow at starting up. :guitar:

---

