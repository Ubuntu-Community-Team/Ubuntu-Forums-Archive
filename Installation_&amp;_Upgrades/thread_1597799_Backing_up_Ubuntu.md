---
title: "Backing up Ubuntu?"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by Mr Tickle on 2010-10-15
Hey Ubuntu members,

In the past I used a program on Windows (back when I used it) to backup the whole computer into one file (disk image) on an external hard drive. Thus when Windows died on my hard drive (corrupt boot file) I could slot in the Acronis disk, boot from that and it would unload the disk image file it made and 're-create' my windows computer.

Unfortunately the Acronis disk only recognises up to the ext3 Linux file system, so I would of done the same if been given the chance :(

I am looking to move my whole Ubuntu OS off my old portable HDD and move it onto a new portable HDD. However as Acronis wont make a carbon copy for me I was wondering what would be the best method for transferring my system across.

Thanks for the help :)


Mr Tickle

---

### Post by andrewc6l on 2010-10-15
The traditional utility for doing this is cpio, which has enough intelligence to create device files as well as regular files, as well as to preserve file ownership.

Nowadays there are probably better choices, but some example cpio commands are here:
[http://adminschoice.com/backup-commands-examples](http://adminschoice.com/backup-commands-examples)

Here's an article on Linux backup:
[http://blogs.techrepublic.com.com/10things/?p=895](http://blogs.techrepublic.com.com/10things/?p=895)

---

### Post by VMC on 2010-10-15
> **Mr Tickle said:**
> ...
Unfortunately the Acronis disk only recognises up to the ext3 Linux file system, so I would of done the same if been given the chance :(

I am looking to move my whole Ubuntu OS off my old portable HDD and move it onto a new portable HDD. However as Acronis wont make a carbon copy for me I was wondering what would be the best method for transferring my system across.

...

The latest Acronis Home 2010 will clone Ext4. I;ve used it many times.

But mostly I use[_Clonezilla_]("http://clonezilla.org/") or [_Partclone_]("http://partclone.org/download.php") to clone my Linux stores.

---

