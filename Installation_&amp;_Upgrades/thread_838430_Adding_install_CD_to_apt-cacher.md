---
title: "Adding install CD to apt-cacher"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by pwaldo on 2008-06-23
Hi all,

I'm using apt-cacher to cache updates to all machines in my home.  Now its time to upgrade to Hardy!  Any ideas on how to get the .debs on the Alternate CD into apt-cacher?  I tried 
```
/usr/share/apt-cacher/apt-cacher-import.pl <CD_IMAGE_MOUNT_POINT>

```but had no luck.  apt-cacher-import.pl is not recursive.

Any thoughts on how to accomplish this?  Thanks in advance!

---

### Post by ajgreeny on 2008-06-23
I know nothing about apt-cacher, but habe you tried mounting the iso on the CD somewhere and using apt-cacher on that folder.  Foe example make a mount point folder in your home called ~/isomount and the mount the Alternate Install CD with
```
sudo  mount -o loop -t iso9660 path/to/file.iso /home/username/isomount
```You may then find that the application will work as you want.

I hope that is not a waste of time, and that what I suggest is helpful to you.

---

### Post by pwaldo on 2008-06-24
> **ajgreeny said:**
> I know nothing about apt-cacher, but habe you tried mounting the iso on the CD somewhere and using apt-cacher on that folder.  

Thanks for the reply!  That is exactly what I did, but apt-cacher-import.pl is not recursive.  The .deb files live in (approximately) dist/pool/a, dist/pool/b, etc., so it did not see the debs :-(

---

### Post by ajgreeny on 2008-06-24
Not even sure if it's possible, as I don't know if you can extract an iso that way, but have you tried extracting (copying) the deb files to another folder somewhere and then using apt-cacher?

---

### Post by liquidweaver on 2009-04-24
[LIST=1]
[*]Mount iso as loopback (makes a "virtual cd-rom drive", if you will)
[*]use apt-cacher-import with recursive and readonly flags
[*]unmount when done
[/LIST]

Details:
sudo mount -o loop ubuntu-9.04-alternate-i386.iso /media/cdrom
sudo /usr/share/apt-cacher/apt-cacher-import.pl -R -r /media/cdrom/pool
sudo umount /media/cdrom

---

