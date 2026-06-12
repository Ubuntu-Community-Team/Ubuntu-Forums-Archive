---
title: "Back In Time Restore Problem"
date: 2011-09-17
forum: Installation &amp; Upgrades
---

### Post by Sidney232 on 2011-09-17
I have just built myself a new machine from scratch and it all works just fine. Now I want to restore stuff from the back up (made using Back In Time) from my old machine. I assume this is possible but I can't figure out how to do it - the snapshots don't appear in the snapshot list.
I need to:
a) restore my /home - including the stuff from other peoples accounts.
b) restore a load of other files - mainly photos.

Any ideas?

---

### Post by ottosykora on 2011-09-17
not sure, but best would be if you indicate with which verson of backintime you did make those backups and what filesystem those backups are on and to what filesystem are going to restore it.

The story is, that the backintime did change in some recent versions in a way, that it tries to preserve all rights in the backup and so it wants to restore them in similar way. 
It used to work on any files system, to and from vfat (fat32) for example, but this does not work any more.
Now backintime needs a file system where the rights can be stored together with the  file or better say in some separate file as they state on their website.

---

### Post by Sidney232 on 2011-09-17
Versions: I made the backups with probably <1.0 and I'm trying to restore with 1.0.6.
All file systems are ext4.
I've read advice saying just edit the host folder name to the new host but not sure I want to try it on one piece of advice only.

---

### Post by ottosykora on 2011-09-17
hmmm, not sure about all that, but I was also not able to use some older backups and even they were present simply not kind of recognized.

This jump to full rights store by backintime is confusing, try to see if they have soemthing on their website.

Worst thing is that one does not get any proper infos or error msg, maximum I got was unable to complete the task or similar.

May be to find somehow a way to install one version before 1.0, but have no imediate idea how to do this.

---

