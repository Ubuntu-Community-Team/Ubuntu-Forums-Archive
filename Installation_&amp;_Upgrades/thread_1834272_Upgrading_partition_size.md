---
title: "Upgrading partition size?"
date: 2011-08-27
forum: Installation &amp; Upgrades
---

### Post by Jason2302 on 2011-08-27
I selected the smallest installation size in Wubi, but now I want to max it out. How can I do this??? I downloaded GParter but don't know what to do. If I need to make a back up, how do I do so? Please, is there a tutorial for a noob or something?

PLEASE help. I have never gotten very good help from this forum but I'm willing to try again.

---

### Post by georgemc on 2011-08-27
WUBI is installed as a file within the Windows NTFS file system so gparted etc most likely will not work.

BACKUP your data!!

See:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

George

---

### Post by Jason2302 on 2011-08-27
> **georgemc said:**
> WUBI is installed as a file within the Windows NTFS file system so gparted etc most likely will not work.

BACKUP your data!!

See:

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

George
I'm backing up now. I just hope I can find a place to back it up to with enough space, unless I can just put it into my /host folder? And then I'm going to reinstall Wubi.

---

### Post by ajgreeny on 2011-08-27
> **Jason2302 said:**
> I'm backing up now. I just hope I can find a place to back it up to with enough space, unless I can just put it into my /host folder? And then I'm going to reinstall Wubi.
As you have obviously realised that Ubuntu is good and you wish to continue with it, why not do it properly with a partitioned install rather than wubi again.

Wubi is not really meant to be a permanent way of installing as a dual boot, but more a way to check the system hardware and whether or not you like Ubuntu.

---

### Post by bcbc on 2011-08-27
[HOWTO: Resize the Wubi virtual disk]("http://ubuntuforums.org/showthread.php?t=1625371")
It's easier than reinstalling, but reinstalling will work too.

PS personally I recommend storing important data on the /host or synch'ing it to the cloud (Ubuntu One). Wubi is great to try out Ubuntu, but all your data is on one file (root.disk) and it's therefore less safe than having it stored on multiple files on the partition.

---

