---
title: "Safe to Partition?"
date: 2008-02-13
forum: Installation &amp; Upgrades
---

### Post by OmegaMB on 2008-02-13
I just wanted to double check: If I were to partition my harddrive and install Ubuntu, would my XP parition be safe and untouched?

---

### Post by jrusso2 on 2008-02-13
If you do it right. Make sure your using the right partition to install ubuntu.  Is your xp occupying the whole drive? If so you will need to shrink that partition.

Also its important to back up first just in case and have all recovery and all install  cd's available.

---

### Post by Pumalite on 2008-02-13
You could use Gparted Live CD to shrink your XP partition.

---

### Post by OmegaMB on 2008-02-13
Do I have to use a different partioner, or would I be able to use the Ubuntu guided partioner without touching the Windows one?

---

### Post by zvacet on 2008-02-14
You will find answer [here](http://www.psychocats.net/ubuntu/installing).

---

### Post by Kevbert on 2008-02-14
With windows you may have a paging file towards the end of the drive.  Run the Windows Defragmentation Program and defrag the drive.  If this block of data has not been moved you'll need to turn off this file.  It can be found at Control Panel - System - Advanced Tab.  Now click on Settings under Performance and select the Advance Tab.  Now click on Change, the Virtual Memory paging file and select the No Paging File radio button.  No click on Set, OK, OK, OK and close Control Panel.
Reboot the machine and then defrag the hard disk again.  There should now be extra room at the end of the disk.
Don't forget to back everything up.
You can now install Ubuntu via the installation CD.  The built-in partitioner can be used.  If you have a guided option (to shrink the existing drive and add the Ubuntu partitions at the end) when you get to the partition part of the program, use that otherwise you'll need to use manual partitioning.

---

