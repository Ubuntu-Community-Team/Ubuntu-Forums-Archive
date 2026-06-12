---
title: "&quot;no root file system&quot; - argh"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by Craigus on 2006-10-27
I'm trying to install edgy from the live CD as my dapper upgrade did not go well. I have:

hda1 - 95 Gb NTFS windows partition, 
hda2 - 500 Mb swap,
hda3 - 9 Gb root,
hda5 - 7 Gb /home (hda4 is the extended partition)

when I try to install edgy using the live CD installer, it keeps saying "no root file system", even though I have told it to mount hda3 as the root mount point and to reformat.

Is this a bug in the edgy installer ?

---

### Post by Craigus on 2006-10-27
Here is the solution:

> The advanced partitioning mode of the installer on the desktop CD has trouble reusing an existing root file system, and will incorrectly claim "No root file system". Since you must reformat the root file system for use by the installer in any case, you can easily work around this problem by deleting and re-creating the partition in question in the advanced partitioner. [WWW] [https://launchpad.net/bugs/67130](https://launchpad.net/bugs/67130)

[https://wiki.ubuntu.com/EdgyReleaseNotes]("https://wiki.ubuntu.com/EdgyReleaseNotes")

---

