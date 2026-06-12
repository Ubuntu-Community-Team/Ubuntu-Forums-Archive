---
title: "Getting an image of linux system"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by charanya15 on 2009-12-19
Hi All

I have my system loaded with Windows and Ubuntu Linux.
I would now want to get the total Image of the Linux Part and then use that to load in my Laptop which i wish to use as Linux Only.
I have installed many things on my existing system which has both windows and linux in it.Now I want to move all those from the linux part on to my new Linux only machine.
ie.I want the exact image of my currently running Linux part of my machine transfered to My Linux Only Machine

Is this possible to do?? If so how?


Thanks In Advance

---

### Post by gadolinio on 2009-12-19
If you have linux in a partition for its own, maybe you can use partimage ([http://packages.ubuntu.com/search?partimage](http://packages.ubuntu.com/search?partimage)). That program creates an image of the partition you point, and can also write it to another one; I have only done the first thing, for backup purpose, but never had to use it.
Once you have installed the program, open a root terminal and type "/usr/sbin/partimage". I don't remember if i did it with a root terminal from my home user, or if i had to start session as root.
It creates an image of the partition in pieces of 2Gib (for example i had a total of 9 files, 2GiB each) in the directory you choose. I assume you'll have to copy all the files to your laptop's hard disk in a live CD session, then install partimage while in live CD, and execute /usr/sbin/partimage (it has the option of writing an image to disk, which i haven't used yet).
Hope you find this useful...

---

### Post by madchine on 2009-12-19
Am I the only getting:

> Package partimage is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package partimage has no installation candidate
when trying to install in Karmic?

EDIT: Universe *is* enabled.
EDIT: Not available for 64 bit architectures it seems :(

---

### Post by lisati on 2009-12-19
You might want to check out [remastersys]("http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys")

---

### Post by phillw on 2009-12-19
Also 

Pybackpack --> [http://www.ubuntugeek.com/pybackpack...x-desktop.html]("http://www.ubuntugeek.com/pybackpack-a-user-friendly-file-backup-tool-for-ubuntu-linux-desktop.html")
Or Clonezilla --> [http://www.tuxradar.com/content/how-...ves-clonezilla]("http://www.tuxradar.com/content/how-clone-hard-drives-clonezilla")

May be of help.

Me ? I'd just cpio the ubuntu area onto removable media & spit it onto the new machine. By using images, you could mess up with disk space. But, I like the command line for doing such crazy things --> [http://ubuntuforums.org/showthread.php?t=35087&highlight=backup](http://ubuntuforums.org/showthread.php?t=35087&highlight=backup)  has the How To for that, if you don't mind rolling up your sleeves.

Phill.

---

