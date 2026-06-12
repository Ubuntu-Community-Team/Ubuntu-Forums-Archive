---
title: "New HD - Copying files vs. new installation + copying files....help!"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by Brian Smith on 2007-09-08
Hi all.
I've managed to copy onto my new larger HD all of my files from my smaller old HD by using thunar and nautilus as root via gksudo.  I'm having permissions problems when I try to boot from the new HD in place of the old HD.  I've modified as many of the permissions as I can find, moving from one folder on the old HD to the same corresponding folder on the new HD.  I've resolved some issues this way, but yet still after I log in as my user, the session closes in less than 10 seconds when a tmp file is attempted to be created, and I'm left back at the login screen.  

So far I've spent probably 4 hours repartitioning the new HD to match the somewhat odd structure of the old one so that my boot, swap, and other partitions are numbered the same when using the new HD, and then copying all of my old files onto the new drive, using the old drive as an external.  (Thank you to anyone involved developing 'testdisk' for saving me when I encountered an error while partitioning causing me to temporarily lose some un-backed-up partitions!) 

What I really want to do is move the older smaller drive to a backup computer and use the new drive in its place on the better main machine.  How much would I lose by reinstalling from the live CD to the new drive, and then copying over my /home directory to the new drive?  Would this "break" some things after I do that copying?  Would I be missing other needed files from other directories?  I've been running this same installation (6.06/Dapper) for 2+ years now, and I've added a number of apps through synaptic, and a few via .deb files as well.  It's not perfect, but it works the way I like it now for the most part.  I'm nervous about finding out a month after I move the old drive to an old system and repartition/format it that something I "need" is no longer available on my system.  Common advice I've seen is to not even try moving an installation, just reinstall.  To me that makes an installation "magic" that happens only one way, not simply a complex system of files that can be replicated.  Using a microsoft operating system, with which I'm more experienced than linux, I would have no problem moving an installation around and resolving any resulting glitches, but I guess I'm just not there yet with linux.  

Has anyone got a good idea/advice about this, or do you need to know specifically which error message I'm presently receiving?

---

### Post by Pumalite on 2007-09-08
You could try a clean installation on the new drive and keeping /home in the old one if you have a separate partition for /home.

---

### Post by Brian Smith on 2007-09-08
> **Pumalite said:**
> You could try a clean installation on the new drive and keeping /home in the old one if you have a separate partition for /home.

I don't have a separate /home partition.

I will on the next new system, I swear it!

Plus, I want to use the old drive somewhere else...

Thanks for the suggestion.

---

### Post by sonofusion82 on 2007-09-08
i would suggest you image the ubuntu partition of old harddisk and then restore the partition image into the new harddisk with tools like clonezilla instead of copying individual files. symlinks, etc will likely cause problem during copying.

anyway, it is always good to keep /home in a separate partition.

---

### Post by Brian Smith on 2007-09-11
> **sonofusion82 said:**
> i would suggest you image the ubuntu partition of old harddisk and then restore the partition image into the new harddisk with tools like clonezilla instead of copying individual files. symlinks, etc will likely cause problem during copying.

anyway, it is always good to keep /home in a separate partition.

Thanks!  Partimage worked well to image the existing installation's 75gig partition into about 47gig worth of gzipped-level compressed files (3.5hrs), then it worked well again to restore the image files into an 80gig partition on the new HD (2.5hrs.)  A new or re-installation would have been quicker, but...I did it this way.

Now....is there a best way to move my /home directory to another larger partition?

---

### Post by Pumalite on 2007-09-11
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by Brian Smith on 2007-09-11
Man, that's a quick response.  I had just found that page and was coming back to say that I had found it, and too late - you've put it up there already!  Thanks many times!  I'll try it out.

---

### Post by Pumalite on 2007-09-11
You are welcome. Have fun!

---

### Post by Brian Smith on 2007-09-22
> **Pumalite said:**
> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Pumalite, the info on that page worked perfectly for me.
I'm loving it, and after a week of heavy usage, I'm pretty sure that everything works as well and as reliably as it previously did.

Thanks!

---

### Post by Pumalite on 2007-09-22
You are most welcome. Glad everything is working fine.

---

