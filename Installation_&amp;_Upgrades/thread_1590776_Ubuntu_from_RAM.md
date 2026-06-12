---
title: "Ubuntu from RAM"
date: 2010-10-08
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2010-10-08
I'd like to set up an Ubuntu from RAM system (but booted from a hard drive).  The idea is at boot time to set up / in RAM (ramfs or tmpfs or ramdisk) and populate it (including everything so that the system can run w/o anything from disk being mounted ... though the data, such as /home, would normally be on disk).  I've done this before derived from Slackware.  The big problem I would see happening is making sure dpkg/apt/aptitude can handle it.  Either they would need to install directly to an on-disk copy that isn't the running system, or they install into the running in-RAM system and that somehow gets copied back to the disk so it is persistent (e.g. do some command, install/ugrade packages, do some command, and it's now at least persistent).

---

