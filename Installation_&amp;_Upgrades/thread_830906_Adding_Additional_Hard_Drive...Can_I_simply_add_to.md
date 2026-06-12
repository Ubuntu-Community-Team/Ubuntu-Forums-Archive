---
title: "Adding Additional Hard Drive...Can I simply add to a pool of storage?"
date: 2008-06-16
forum: Installation &amp; Upgrades
---

### Post by i.wanna.corndog on 2008-06-16
Hey,

I am currently running Ubuntu Server on a small PC as a media server and I am running out of space. Is there any way to add a second hard drive and simply have the contents of the first spill over once it is filled? I know that, for example, Windows Home Server allows you to add hard drives in a "pool" without too much hassle, and I'm wondering if I can do the same.

If not, should I just set the new hard drive to mount at a new folder and move some of my shares to that drive?

Thanks!

---

### Post by i.wanna.corndog on 2008-06-17
Bump.

Anyone?

---

### Post by wraezor on 2008-06-17
If you setup your original storage as LVM, you can easily add another disk as a 'physical volume' which you add to an existing 'volume group'.

If you didn't, you could still do it, but it would be a bit more work:
 1. Add your new disk
 2. Setup as LVM physical volume, then build your volume group and logical volume on top of that.
 3. Move all your data from your existing location to the new one. (Presuming the new one is large enough)
 4. Blow away your old partition
 5. Recreate it as a physical volume and add to the volume group.

---

### Post by bkline on 2008-06-17
There's another possible solution to your problem if you don't want the addition complexity of LVM, depending on how your data is laid out.  You take the part of your file system that's grown beyond your original projections and just move it to a partition on the new disk and mount it back to a mount point in the root file system.

Here's a hypothetical example (making this up since I don't really know how your system's laid out).  Let's say you started out some time ago with a 60GB drive to set up the media server, with expectations that this would take care of users' needs for the foreseeable future.  The interesting content in this scenario is in a DBMS which stores its data under /var/lib.  Using du on /var/lib shows you that it's taking up half the disk, and isn't leaving a lot of room for system administration, backups, user files, etc.  So for [$80]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=3564505&Sku=TSD-500AS5") you pick up a new 500GB drive which you drop in, partition, and format with your favorite Linux FS.  You boot into the machine from a LiveCD (to make sure there are no changes to what's on /var/lib while you're doing this), mount the original and new partitions, copy everything from /var/lib to the new partition, rename /var/lib to /var/oldlib, mkdir /var/lib, add mount instructions to /etc/fstab to mount /dev/whatever to /var/lib, then reboot.  The incentive to do things this way isn't quite as dramatic as the ratio between the size of what you've already got and the size of what you're going to add decreases, and the ratio of the portion of the file system you'd move to the rest of the original disk is too large, but given the cost of disks these days, it's common to be able to afford a much larger disk than what you started with a few years ago.

I've done something like this a few times when I've found myself in a position similar to the one you're in.  It's possible you can get away with doing this without the LiveCD, by booting into single-user mode and making sure no processes are running which might mess with /var/lib, but mounting everything from another copy of Linux is safest.

I did try the LVM route once, but I didn't understand enough of what was going on under the covers not to get burned, so I've stuck with the method described above since.

Hope this helps.

Cheers,
Bob

---

### Post by i.wanna.corndog on 2008-08-12
Sorry to bring up an old thread, but I just wanted to say thanks to bkline and to clarify on what you're saying.

Here's my setup: I ripped my movie and TV show collection to my media server. I have a folder for movies (/share/movies) and a folder for TV shows (/share/shows). What you're saying is that I could put in a new drive, format the drive, copy everything from the shows folder to the root of that drive (from a live CD), then rename the shows folder to something like /share/oldshows. After this, all I would need to do is to have the newly partitioned drive mount in /share/shows, right? Then, I'm assuming I could just delete the /share/oldshows folder.

I think I'll give it a try in a few days. If you're still around to confirm this, that would be great!

Thanks for all the help, guys. This is why I love the open source community :)

---

