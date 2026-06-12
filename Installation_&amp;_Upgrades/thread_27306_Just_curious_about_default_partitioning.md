---
title: "Just curious about default partitioning"
date: 2005-04-15
forum: Installation &amp; Upgrades
---

### Post by fluidity on 2005-04-15
Hello dear knowledgeable Ubuntu users,

I'm not really experienced under Linux and I just installed Ubutu 5.04. Everything went smoothly, but I wonder why the default partitioning program creates an extended partition to hold the swap space. No problem with that, I'd just like to understand...

thank you

---

### Post by Ti-Paul on 2005-04-15
Linux ALWAYS need a swap partition... normally twice the size of your ram...

Windows is also using a swap, but it creates a file on your C: drive... (not better since it is using your C:  partition space)

I'm not a SWAP-Geek so i don't know all the "under-the-hood" thing of it, but i know that it needs it and it's working very well like this!  \\:D/

---

### Post by fluidity on 2005-04-16
Thank you Ti-Paul,

I did not state my question well enough, sorry. I wonder why the swap partition has been placed in an EXTENDED partition instead of a PRIMARY partition.

I have let the installer use ALL my hard drive, no dual booting. It has made a boot partition hda1 with the most of the hard disk space, then an extended partition hda2 in which it has created the swap partition hda5. Why not just use hda2 as a normal partition for the swap space ?

---

### Post by Ti-Paul on 2005-04-16
Humm... Good question for something i don' t want to know!  :grin:

---

### Post by Gary Powers on 2005-04-16
[QUOTE=fluidity]Thank you Ti-Paul,

I did not state my question well enough, sorry. I wonder why the swap partition has been placed in an EXTENDED partition instead of a PRIMARY partition.

I have let the installer use ALL my hard drive, no dual booting. It has made a boot partition hda1 with the most of the hard disk space, then an extended partition hda2 in which it has created the swap partition hda5. Why not just use hda2 as a normal partition for the swap space ?[/QUOTE]

I believe it may be due to limits on the number primary partitions permitted ont he drive.  Pointless to waste one on a very small sway drive.

Gary

---

### Post by lgb on 2005-04-16
Disks have more sectors on the outer tracks. With a constant number of RPMs this leads to a better performance on the outer tracks vs the inner ones on the disk.

---

### Post by fluidity on 2005-04-16
[QUOTE=Gary Powers]I believe it may be due to limits on the number primary partitions permitted ont he drive.  Pointless to waste one on a very small sway drive.

Gary[/QUOTE]

As far as I know, the maximum number of partitions is 4. Among these 4, ONE can be an extended partition. So the installer actually wastes this secondary partition! Furthermore there are still 2 left possible partitions for the drive, which is pointless as the drive space is fully used anyway... Hummmm there must be some other reason 
:-k

---

### Post by lgb on 2005-04-16
[QUOTE=fluidity]As far as I know, the maximum number of partitions is 4. Among these 4, ONE can be an extended partition. So the installer actually wastes this secondary partition! Furthermore there are still 2 left possible partitions for the drive, which is pointless as the drive space is fully used anyway... Hummmm there must be some other reason 
:-k[/QUOTE]

Actually you are allowed 4 primary partitions and up to 59 logical partitions  on an  IDE  drive. ;-)

---

