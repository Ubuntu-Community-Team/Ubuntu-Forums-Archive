---
title: "How to know what to backup"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by pinkunicorn on 2007-10-18
Is there an easy way to get a list of all the configuration files that have been add/modified? I'd like to know what files under /etc/ (mostly, at least) that I need to make backups of in order to be able to replicate a server.

A list of what packages have been installed apart from the standard ones would also be nice.

---

### Post by dilney on 2007-10-18
A quick way to backup your settings is with sbackup ([http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html](http://www.ubuntugeek.com/backup-and-restore-your-ubuntu-system-using-sbackup.html)).

I personally back up all /etc (you can choose to restore individual files or subfolders later).

As for the packages, a quick way to backup what you have installed is with APTonCD.  Not only does it list all your packages, but also creates an ISO containing all the packages you have installed and a metapackage to reinstall them.

On a side note, this is my first post on this forum :)  (I've used Linux many years ago, was away for a while, and finally came back and migrated fully to Ubuntu.)

---

