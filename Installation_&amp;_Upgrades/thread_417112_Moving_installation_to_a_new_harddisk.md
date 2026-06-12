---
title: "Moving installation to a new harddisk"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Steve Smith on 2007-04-21
I've got my webserver working just how I want it, but the harddisk's making a funny scraping noise, so I'm getting a new one!  I want to move everything to the new disk.  From Googling I've found I should move the boot sector first using dd, partition the disk with a livd cd then do cp -a to move everything across, maintaining permissions.  So, my questions:

1. does this seem a good way to do it?
2. could I just install Ubuntu to the new disk, then copy the entire filesystem off the old disk, overwriting everything?
3. how do you use dd to copy a boot sector?  I've never used it before and as much as i can look at man pages I don't want to screw up my boot sector on my first attempt!
4. does cp -a maintain owner group names?

an aside:
5. how do you make Google search for "cp -a", insisting it sees the dash?!

Thanks very much! :)

---

### Post by Scunizi on 2007-04-21
If you have a graphical environment on the server you might consider installing vmware player or server and using "Personal Backup Appliance".  It will work from one machine to another over a lan or on the same machine to a usb drive.  I've used it with ubuntu and windows 200pro.  Worked like a champ and painless.

---

### Post by Steve Smith on 2007-04-22
Thanks, but no GUI I'm afraid!

---

### Post by IgnorantGuru on 2007-04-22
This is my preferred method...
[http://ubuntuforums.org/showthread.php?p=2148017#post2148017](http://ubuntuforums.org/showthread.php?p=2148017#post2148017)

---

### Post by mlind on 2007-04-22
1. I'd say no.
2. Yeah, but you should either clone existing system, or install from scratch and cherry-pick files from old install (like configuration files). 
3. I'd use **grub-install** script instead of dd.
4. You'll have problems with "special" files though. Use cpio (or tar instead).


I've succesfully used cpio (and tar) to backup the partitions in the past. cpio should be used if you're backing up a root partition. tar is probably enough for /home partition.

[http://sdn.vlsm.org/share/Debian-Doc/manuals/debian-reference/ch-tips.en.html#s-archiving](http://sdn.vlsm.org/share/Debian-Doc/manuals/debian-reference/ch-tips.en.html#s-archiving)
[http://bradthemad.org/tech/notes/cpio_directory.php](http://bradthemad.org/tech/notes/cpio_directory.php)

---

