---
title: "Moving users from an old server to New Ubuntu server"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by gdselzer on 2006-07-03
I have a Mandrake 10 box (OLD) that I am using as a home server (web, samba, ftp, firewall, etc.) and a new box with a fresh install of Dapper and MythTV from SVN (NEW).  I would like to consolidate everything into NEW and donate the old box to the local elementary school.  I obviously have a list of things to work on, but the first thing I'd like to do is move some of the users on OLD to NEW.  There are approximately 30 family, friends, etc. setup as users for FTP and Web Access (as well as a half dozen groups).  

Manually adding all the users and dealing with passwords seems like an administrative challenge that I'm not up to.  Additionally, I don't think I want to just copy the passwd, shadow, and group files from OLD to NEW.  I would think that given the differences in the distributions, the system users would be different.  

Is there a good way to export/transfer/move users from one box to another without moving ALL users?  Or alternatively, is moving all users fine?

Thanks

---

### Post by gdselzer on 2006-07-04
bump;)

---

### Post by kzutter on 2006-07-05
I am watching this thread as I have a similar job coming up. Not as complicated as yours - mostly samba file server users. A couple of admins have access to other services - I may have them re-create their own user space. 

Here is my basic plan

Copy pertinent parts from passwd, shadow, and group files (i.e. users with numbers 501+)

adjust any groups ( i.e. ftp group on one machine may be ftpusers on other)

recreate user's home dirs and shared data dirs (copy data - fix permissions)

copy smb.conf to new box 

TODO - see if smbpasswd file can be copied straight over.

make sure samba users cannot log into shell - and those that are allowed, can

In other words, test, fix, test, fix , test, repeat....

---

### Post by gdselzer on 2006-07-05
You hit it on the head.  I ended up just copying the relevant users from passwd, shadow, and group.  It seems to have worked.  

My Samba move will be coming up soon as well.  Good luck.

---

