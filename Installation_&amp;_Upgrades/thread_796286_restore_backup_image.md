---
title: "restore backup image"
date: 2008-05-16
forum: Installation &amp; Upgrades
---

### Post by butterman on 2008-05-16
I need assistance restoring a backup disk image created using partimage and [these instructions]("http://www.psychocats.net/ubuntu/partimage").  I attempted to upgrade an old P3 server running dapper but hosed the machine (kernel panic).  Now I want to restore my dapper backup image.   

So far I've done the following:

connected an external USB drive to the old P3 server that contains the backup images
booted the old P3 server using a rescue cd (which includes partimage).
noticed numerous buffer i/o errors during a long boot process
entered "df" to check whether the external drive mounted automatically--it didn't
ran:
```
mkdir /mnt/sdc1
```
```
mount -t ext3 /dev/sdc1 /mnt/sdc1
```
Ran partimage
```
partimage
```
Selected sda1 to restore and followed [these instructions]("https://wiki.ubuntu.com/Testing/Backing_Up").
After identifying the image to be restored, I hit F5 to continue.
Partimage terminates with the following error: "invalid compression level for /mnt/sdc1/atlas-backup-image/atlas-sda1.000"  This partition is about 3G.

Are my partitions too big?

Part II - I purchased a new duo core machine and plan to migrate the server settings from the P3.  Can I restore these images on the new machine?  Should I try upgrading the P3 again before migrating?  Should I do a clean install of 8.04 on the new machine and then try to migrate the application settings?

---

### Post by Pumalite on 2008-05-16
This might help:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)

---

### Post by butterman on 2008-05-16
That link happens to be the one I used to create the backup image.  The problem I have now is restoring it.  The only instructions for restoring the image are: "The restore process is very similar except that you choose the Restore partition from an image file option when PartImage launches."  I did this in my attempt to restore the backup image but I'm getting an "invalid compression" error.

It seems that I'm not the only one with this problem.  This [link]("http://www.partimage.org/forums/viewtopic.php?t=213") suggests that just renaming the image with a .gz extension will overcome the error while others say this is a bug in partimage for partitions over 2GB.

---

### Post by butterman on 2008-05-17
Okay, here's the solution:

1. boot with system rescue cd
2. create mount point
```
mkdir /mnt/sdc1
```
3. mount external usb drive
```
mount /dev/sdc1 /mnt/sdc1
```
4. rename the backup image
```
mv atlas-sda1.000 atlas-sda1.000.gz
```
5. restore the backup image
```
gunzip -c atlas-sda1.000.gz | partimage restore /dev/sda1 stdin
```

This [link]("https://wiki.ubuntu.com/Testing/Backing_Up") says the mbr must be restored separately.  I tried restoring the mbr using the same technique but got an invalid compression error. 

```
gunzip -c atlas-sda1.000.gz | partimage restmbr /dev/sda1 stdin
```

Even with executing this command successfully, the machine rebooted properly.

---

