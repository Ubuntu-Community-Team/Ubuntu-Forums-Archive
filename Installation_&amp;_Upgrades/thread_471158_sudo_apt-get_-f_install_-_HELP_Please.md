---
title: "sudo apt-get -f install - HELP Please"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by yubayogi on 2007-06-11
Hey Guys-

I am trying to get some software instaled on the Ubuntu-server edition. 7.04 (I recently downloaded and installed)

When I type "apt-get -f install" I receive a list of files/pachages that need to be installed:

libx11-6, libx11-data, etc. (which seems normal)

Then it asks me for permission to unpack and use more disk space I type "Y".  

Then it says insert Ubuntu-server 7.04_Fiesty Fawn_-release i386 (20070415) in the cdrom drive and hit enter.

----------This is where I am stuck--------------- It doesn't recognize the iso cdrom I just used to install with.

I installed from the iso I made from the download and it seems like the os works, I can ping, ftp, and apache works.  

**[SIZE="4"]My question is:  Do I have the wrong cd disk?  Do I need to unpack something for it to recognize the files?  [/SIZE]**

Please help, I am stuck, I can't install anything.

Scott

---

### Post by One Quick Question on 2007-06-11
Have you mounted the cd?
Check out the man page for apt.conf, specifically towards the middle where it talks about cdroms.

> 
cdrom 
 CDROM URIs; the only setting for CDROM URIs is the mount point, cdrom::Mount which must be the mount point for the CDROM drive as specified in /etc/fstab. It is possible to provide alternate mount and unmount commands if your mount point cannot be listed in the fstab (such as an SMB mount and old mount packages). The syntax is to put 

"/cdrom/"::Mount "foo";

 within the cdrom block. It is important to have the trailing slash. Unmount commands can be specified using UMount.


---

