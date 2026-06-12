---
title: "Read-Only File System and Grub"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by mkaylor on 2007-07-24
Using 7.04 I started to create a MythTV machine and somehow I managed to get my myself in a bind.  The machine started booting up as a Read-Only File System.  Couldn't edit a darn thing!

I figured it was something I did in the fstab and I did find a mistake in their.  So I booted off a CD and fixed those error.  After rebooting it still would not go back to it's normal self.  Being an engineer/tinkerer, when it booted I changed the ro quiet splash to an rw in the grub boot line and now everything is fine.  It boots like it should and the Penguin gods smiled down upon me.

I then went to the grub manual and I couldn't find anything about the ro setting.  What is that for and why did it fix my problem?  All my other machines are set to ro and they don't have this problem.

Is their something else I should do to fix this the proper way?

---

