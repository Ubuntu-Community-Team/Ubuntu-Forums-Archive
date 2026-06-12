---
title: "No clue how to partition my drive for dual-booting"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by ultimania92 on 2008-10-18
I want to use Windows XP and Ubuntu together, and I tried to install using the installer the Live CD has. I got to step 4, and have no idea how to partition the disc. The Guided install doesn't help a bit, so I want to manually do it. I see my only hard drive, a SATA drive that is ntfs file format and has 250GB of space on it. I have roughly 100GB of space left, and I want to allocate 60GB for Ubuntu. I can't seem to reduce the size of my drive, and I don't want to go through reformatting my drive and wiping everything off of it. I have an external hard drive, and I backed up all of my documents, my Steam folder, my torrents, everything is backed up.

The problem I'm getting is trying to get more space for my drive, but the drive thinks there's only 8MB of free space left, and the whole 250GB is allocated for Windows XP.

Computer specs are as follows:
-2GB RAM
-Intel Core2duo @2.4ghz
-GeForce 9600GT
-250GB SATA hard drive

Anyone got a clue as to what is going on?

---

### Post by BGrigg on 2008-10-18
Give this site a read (and a bookmark!):

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by ultimania92 on 2008-10-18
Ok, i gave that page a look, but the thing is, I can't resize my hard drive, because the windows install takes up the entire drive.

---

### Post by theduffman on 2008-10-18
> **ultimania92 said:**
> Ok, i gave that page a look, but the thing is, I can't resize my hard drive, because the windows install takes up the entire drive.

the installer can resize it i think (never tried myself)
also a gparted livecd will do the job too

---

### Post by ultimania92 on 2008-10-18
> **theduffman said:**
> the installer can resize it i think (never tried myself)
also a gparted livecd will do the job too
I get errors when trying to use Gparted and use the guided resize tool. It isn't allowing me to resize my windows partition. There's no option to resize my current partition

---

### Post by theduffman on 2008-10-18
> **ultimania92 said:**
> I get errors when trying to use Gparted and use the guided resize tool. It isn't allowing me to resize my windows partition. There's no option to resize my current partition

well there are good commercial tools if you wanna go down that route... like Acronis Disk Director, and Acronis TrueImage which can resize for you.. 
erm.. maybe another option is to use a backup tool to backup the xp partition, then delete/repartition it with gparted livecd and restore the xp partition to the now smaller partition.. i know ive done this with trueimage bootcd.

last resort, you could just reinstall windows, and repartition it from the installer

---

### Post by nerak on 2008-11-01
I'm actually having the exact same problem.  Ultimania, did you ever figure it out?

---

