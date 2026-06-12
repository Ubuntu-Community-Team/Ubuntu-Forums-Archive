---
title: "transfer from IDE to SCSI server"
date: 2010-07-11
forum: Installation &amp; Upgrades
---

### Post by rompstar on 2010-07-11
I have a IDE hp server with a single IDE drive as primary (and a 2nd external UBS drive) is setup to backup the server.  Anyways, I got a better server now, it has 2 SCSI drives that are RAID controlled, so each one copies it self for backup, incase 1 drive goes out, it still works.

I would like to transfer the data to this new server and take my main server down for maintenance and hard-drive upgrade (cuz it only has 100GB and I want to put a much bigger drive for lots of photos and videos, like 1Terabyte.

Currently the external backup drive, copies these files:

/etc
/home
/usr
/var

both have 10.04 running on them, not sure about the UUID and how all that works.

What is the best way to transfer the data to the new server ?  Should I do a install from a DVD and then later do a restore using those 4 folders ?

---

