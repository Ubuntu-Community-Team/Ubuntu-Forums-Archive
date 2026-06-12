---
title: "can not add DVD repository"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by zukro on 2011-07-16
i am new to ubuntu 11.04.

i use DVD repositories (8 DVDs) because of my extra low speed internet connection,
each time i insert DVD, it will be automatically scanned/indexed by synaptic package manager.
but unfortunately it miss 2 DVDs, so i tried to add DVD repository manually:

1. by using synaptic package manager
EDIT > ADD CD ROM> insert DVD

and the result:
E: Unable to stat the mount point /media/cdrom/ - stat (2: No such
file or directory)
E: Unable to stat the mount point /media/cdrom/ - stat (2: No such
file or directory)
E: Failed to mount the cdrom.

2. by using terminal
sudo apt-cdrom add

and the result:
E: Unable to stat the mount point /media/cdrom/ - stat (2: No such
 file or directory)
 E: Unable to stat the mount point /media/cdrom/ - stat (2: No such
 file or directory)
 E: Failed to mount the cdrom.

is there anyone can help me?

---

### Post by ADani on 2011-10-11
The same thing happens to me, sorry, but I don't yet know how to solve it, I'm quite noob too
Apparently the problem is the repository is looking for the CD in the wrong place
maybe this helps:
[http://ubuntuforums.org/showthread.php?t=661090]("http://ubuntuforums.org/showthread.php?t=661090")
>  You could insert the ubuntucd or change your repositoryconfig from apt-get to look somewhere else for the required packages

hope it helps

---

### Post by zukro on 2011-10-11
i solved the problem  insert your DVD and type this on terminal  sudo mount /dev/cdrom /media/cdrom

---

