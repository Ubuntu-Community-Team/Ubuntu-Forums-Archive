---
title: "Installation Issues: Partitioner stuck at X%"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by SaintJohnShawn on 2007-10-19
Hi everyone,

I'm trying to get help installing Ubuntu 7.10.  I currently have Vista x64 installed; however, I left about 30gig of unallocated space for Ubuntu.

I have downloaded and burned both the Alternate and Desktop x64 versions of Ubuntu 7.10.  I've checked the MD5, burned at 4x (verified), then checked the disc for errors (none found).

With the desktop CD, the partitioner gets to 50% (scaning disks), but never moves again.

With the alternate CD, the partitioner get to 38% (scanning disks), but never moves again.

Prior to repartitioning my hard drive, I had Vista x64 and Ubuntu 6 (installed with no issues).

Any ideas why this version can't get past the partitioner?  Has the partitioner changed?

---

### Post by SaintJohnShawn on 2007-10-19
Hi everyone,

I'm trying to get help installing Ubuntu 7.10. I currently have Vista x64 installed; however, I left about 30gig of unallocated space for Ubuntu.

I have downloaded and burned both the Alternate and Desktop x64 versions of Ubuntu 7.10. I've checked the MD5, burned at 4x (verified), then checked the disc for errors (none found).

With the desktop CD, the partitioner gets to 50% (scaning disks), but never moves again.

With the alternate CD, the partitioner get to 38% (scanning disks), but never moves again.

Prior to repartitioning my hard drive, I had Vista x64 and Ubuntu 6 (installed with no issues).

Any ideas why this version can't get past the partitioner? Has the partitioner changed?

---

### Post by Pumalite on 2007-10-19
Ubuntu cannot install in 'unallocated' space.

---

### Post by SaintJohnShawn on 2007-10-19
Sorry, posted it in the installation forum now:  [http://ubuntuforums.org/showthread.php?p=3570651#post3570651](http://ubuntuforums.org/showthread.php?p=3570651#post3570651)

Haven't seen a way to delete posts, please delete this topic, the one above is the correct forum.

---

### Post by Technoviking on 2007-10-19
Do you hear any clicking? It maybe a bad hard drive. 

Also try running gparted from the System menu on the live CD, and see if it can create the partitions for you.

---

### Post by Technoviking on 2007-10-19
Threads merged.

---

### Post by SaintJohnShawn on 2007-10-19
I started up System->Partition Editor (GParted).

It just says "Scanning all devices...", the bar moved from left to right, over and over again.

With the last version of Ubuntu, when I installed, it was right away, and I was able to tell it to install into my unallocated space (it made the partitions automatically in the installer).

Ideas?

---

### Post by SaintJohnShawn on 2007-10-19
Sweet, it eventually came up.  Should I try to make partitions in this interface?

---

### Post by SaintJohnShawn on 2007-10-19
Thanks everyone for the suggestions.  

I finally figured it out.  I had my ipod and a usb drive plugged into the computer.  My guess is that it wasn't so much the ipod, but likely the usb drive.  I had been using it as a ready-boost drive in Vista.  Hopefully anyone else having the same issue can make sure they have all usb drives and such unplugged before installing.

---

