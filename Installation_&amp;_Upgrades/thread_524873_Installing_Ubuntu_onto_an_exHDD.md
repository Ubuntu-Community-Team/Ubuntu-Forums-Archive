---
title: "Installing Ubuntu onto an exHDD"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by IrishKnight on 2007-08-13
I'm having bother installing Ubuntu onto my new "My Book".  It comes up saying that it was unable to mount it or something.  At the partition part of the set up I noticed a lock beside the partition.  I'm guessing this is where the problem lies.  Can anyone help me out?  The exHDD I'm using is Western Digital My Book Essential Edition 500GB USB2.0 fyi.

---

### Post by logos34 on 2007-08-13
Actually a lock symbol means it's mounted.  But it needs to be **unmounted** for resizing, formatting and installation.  (it's probably formatted fat32 or ntfs, and you're going to have to change that to ext3 for linux)

Go to Menu bar>Preferences>Removable drives and storge

ont he "storage" tab uncheck "mount removable drives when hot-plugged" (uncheck the other boxes on that tab for good measure)

now go through the installation and create your partitions

---

