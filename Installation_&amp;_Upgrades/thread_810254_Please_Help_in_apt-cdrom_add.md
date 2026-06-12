---
title: "Please Help in apt-cdrom add"
date: 2008-05-28
forum: Installation &amp; Upgrades
---

### Post by deepblue_tiano on 2008-05-28
Hello everyone I dont know whats the problem with my ubuntu 7.10. I planned to upgrade it to 8.04 using alternate cd but, I cant add cdrom in repository.. I got this error..

E: Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)

E: Unable to stat the mount point /cdrom/ - stat (2 No such file or directory)

E: Failed to mount the cdrom.

---

### Post by Mark_in_Hollywood on 2008-05-28
First: Double check that your CDROM is working.

Second: Go to Places/Computer/<your cdrom device name> and see if it's mounted. If it is not mounted:

sudo mount -a

check that the drive mounted. If it is mounted, go to the next step.

Third: If the CDROM can read, go to System/Administration/Software Sources, again and try adding the CD.

---

