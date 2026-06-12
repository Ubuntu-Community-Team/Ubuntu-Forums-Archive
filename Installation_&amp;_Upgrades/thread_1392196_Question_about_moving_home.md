---
title: "Question about moving /home"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by kgriff on 2010-01-27
I'm attempting to move /home on my wife's computer to a different partition.  I'm following the psychocats tutorial at [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)
When I get to point where I'm moving all of the files from /home to the new folder, and I execute
find . -depth -print0 | cpio --null --sparse -pvd /new/  (in my case it is /mnt/newhome)

I get the following:
cpio: cannot make directory `/mnt/newhome//./username': Permission denied
cpio: /mnt/newhome//./username/.pulse/volume-restore.table: Cannot open: No such file or directory

I get this for every file and directory in /home.  I have tried running the command as sudo, but I'm note even prompted for a password.

Can anyone help?

---

### Post by wmcbrine on 2010-01-27
When I've done this is the past, I just used cp:

cp -a -x /oldhome /newhome

if I'm remembering correctly (but consult the cp man page for yourself).

---

### Post by flabdablet on 2010-01-27
find/cpio is old-school standard practice. It's worth knowing how to use cpio if you're going to do any admin work on Unix boxes that don't have the GNU toolset installed; non-GNU versions of cp quite routinely do the Wrong Thing.

In any GNU/Linux system, including Ubuntu, cp -ax will work just fine.

---

### Post by Dogalot on 2010-01-27
I have a simular question (or maybe not).  Recently my GDM became corrupted, and I needed to reinstall 9.10.  It created a new partition.  I can use the Disk Manager to get to the other partitian and see the files, but I am unable to do anything with them.  I'd like to change the permissions so I can burn them onto a CD (to back them up), then wipe the whole drive and start over.  I get the same message Permission Denied.  

I can log into the old version, on the old partitian in terminal... but I don't know what commands to use to make all the files available to the 'new' system.

Can anyone help?

---

### Post by oldfred on 2010-01-28
This has instructions:

You need to make a mount point and mount it with correct permissions or change permissions after mounting:
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)

$ sudo mkdir /Data
$ sudo mount /dev/sda5 /Data
where sda5 needs to be your drive, partition
if not known to list partitions
sudo fdisk -l

If you cannot read and write then change the permissions.

$ sudo chmod -R 777 /Data
sudo chown -R fred:fred /data
where fred should be your name

---

