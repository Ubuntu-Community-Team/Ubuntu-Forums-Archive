---
title: "Unable to install libc6-dev"
date: 2010-03-28
forum: Installation &amp; Upgrades
---

### Post by shawnerz on 2010-03-28
All,
I'm trying to install libc6-dev with the 64 bit version of Hardy (8.04.4).
I have the Hardy burned on a CD-RW and the CD is in the drive.
When I type sudo apt-get install libc6-dev I get the following
```
The following NEW packages will be installed:
  libc6-dev
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2538kB of archives.
After this operation, 11.5MB of additional disk space will be used.
Media change: please insert the disc labeled
 'Ubuntu 8.04.4 _Hardy Heron_ - Release amd64 (20100121.1)'
in the drive '/cdrom/' and press enter
```

Everytime I hit <enter>, I keep getting the message "Media change: please insert the disc labeled..."
The CD is in the drive.  In System | Administration |  Software Sources, everything is enabled.  The Third Party Software tab has he cdrom checked, the archive locations for Hardy, and one for Wine.

Any ideas?

---

### Post by shawnerz on 2010-03-28
I fixed my problem.  I don't know why it worked, but it did.
I went to System | Administration | Software Sources | Third Party Software.  I selected the first entry and hit Remove.
The software Source list then went through a bunch of updates.  I then tried to install libc6-dev, and it magically worked.

---

