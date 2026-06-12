---
title: "Problems after upgrade 8.4 to 10.4"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by tx836519 on 2011-03-26
Hi All,

I have been delighted with the operation of Ubuntu 8.4 (hardy heron) and finally upgraded my network to Ubuntu 10.4 (lynx).  All went pretty well where most of the problems were small and easily fixed.  One that is a bit troubling is with the operation of BackupPC.

I have been running with no problems for quite some time using the sudoer's technique for BackupPC to log into a host and then sudo to do the backup with a limited command set.  After upgrade, the rsync clients are working fine, but the localhost backup of /home on the archiving machine using tar is having permission problems.  The security environment has been enhanced since version 8.4.  Is there something that I need to do to get backuppc user the right permissions to do a tar backup of localhost?

Thanks in advance for any assistance.  -- ken

---

