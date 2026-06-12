---
title: "Can't add normal user during install"
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by kmoz on 2005-10-18
Installing Breezy on a new box.  I"ve already successfully installed on a different machine with the same cd i'm using now.  During the install, I'm prompted to setup the regular user info (Name, account name, password 2X).  I do this, hit enter, and then am brought back to the add user screen.  I can't add a user during the install process.  Any help here?

I just thought of something that might be giving me issues.  I have 2 HD's in this box.  The first is 20gigs, with 3 parts - 15 gigs for winXP, 750megs for swap and the rest for / of ubuntu

the second HD is 6 gigs formatted as /home - I wanted to be able to use a common My Documents/ "/home" drive as I switch back and forth quite often between the 2.  Is ubuntu unable to makea  /home/user directory on FAT32?  I'll try changing it and seeing if that works.

anyother suggestions are still welcome

---

### Post by kmoz on 2005-10-18
So I guess file this one under quasi-newb issue.  Changing the 2nd drive to ext3 allows installation to continue without issue.

I guess the lesson here is, FAT32 can not be used as the format for /home directories.  I realize this could represent a security issue, but why can't I decide this for myself?  is there a way to have a FAT32 partition as a home directory?

---

