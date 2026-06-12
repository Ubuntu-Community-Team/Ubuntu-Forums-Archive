---
title: "Making partitions"
date: 2013-02-20
forum: Installation &amp; Upgrades
---

### Post by chrisguk on 2013-02-20
Hi,

I guess this may be a server question but I believe it applies to desktop as well.

I recently had a problem with my 2TB drive in that I have Ubuntu server installed on it and all my media, for example movies were held in a folder called "share".  For some silly reason I deleted everything in /var/lib, call it a slip of the key.  I found that I needed to reinstall everything and move the media to another drive while I did this.

Someone mentioned to me, "why dont you create two partitions?, and then use one small one for the operating system and the other for the media?"

I assume this way then if the OS goes down again all i have to do is make a new install on the OS partition instead of transferring everything.

Is this a good way to do it and whats the best approach to achieve this?

---

### Post by Mark Phelps on 2013-02-20
That approach is overly simplistic because while you might be able to isolate the "OS components" in one partition, while having media files in another, applications pose a whole different problem.

Why?

Because they get installed in various different directories across the filesystem. It's not a simple matter to tell an app installer to use a directory (like, for example, on your "media" partition) and in some cases, you don't have ANY say where the components get installed.

Some folks might claim you can accomplish this by having "/home" on its own partition -- but that is only partly true because not all the components of an installed application are going to get written under /home.

It's a similar problem to folks in MS Windows thinking they can move "Program Files" to a separate partition ... only to then learn that the Registry (which is actually a collection of files) stays behind in the "OS partition" -- thus preventing the migration of apps outside the OS partition.

---

### Post by chrisguk on 2013-02-20
So, with this in mind could I use for example a fresh 2TB drive.  Boot up Gparted Live CD and create two partitions on this drive, lets call them sda1 and sda2.

sda1 - 30GB
sda2 - the rest of the available space

install Ubuntu Server on sda1

would that be a feasible solution?

---

### Post by darkod on 2013-02-20
Depends what you are trying to do. If the data is strictly photos/music/movies, yes.

Put it on any partition and with custom mount point, and when formatting / and reinstalling, the data stays on your data partition and is completely usable.

For example create /data mount point, and later share it in samba or share subfolders in it, depending how you want to organize it.

---

