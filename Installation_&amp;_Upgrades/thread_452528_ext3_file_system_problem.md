---
title: "ext3 file system problem"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by artesvida on 2007-05-23
I'm trying to install Ubuntu server (6.10) on a spare PC.  This is just for testing purposes, so I just grabbed a spare off the shelf to install.  This system had a single partition, NTFS format, Windows 2000 installed.  I start the install, it gets to the file system format, and it fails.  System hung during format, so it looks like a bad disk.  I get a another PC (same model, same partition setup), start the install, gets to file system format, and... it fails.  I step back to look at the partition setup, verify a few things, try again, and it fails again.  Okay, another bad disk perhaps.  I get a THIRD one, start the install, and the file system format fails.  I step back, change the root partition to ext2 instead of ext3, the format succeeds and the install continues.

Is there something I should know about using ext3 file systems on IDE drives?  These are all (essentially) identical Gateway E-4000 systems.  Is there something I did wrong in the process that made the ext3 format fail?

---

