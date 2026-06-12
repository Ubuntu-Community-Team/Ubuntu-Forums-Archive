---
title: "Increase in Size for VirtualBox"
date: 2011-03-16
forum: Installation &amp; Upgrades
---

### Post by anuraggautam on 2011-03-16
I would like to increase the size of virtualbox, can any one help me how to do that.

Also my Virtual Size is reflecting as 20 GB  & 
Actual Size is reflecting as 11.99 GB

and in My Computer free space is reflecting as 3.4 MB.

Can i know how to increase the size ?

I am attaching the screen shot below for more details.

Regards,

---

### Post by lkraemer on 2011-03-17
I think you really meant that you wish to resize your VDI (Virtual Disk Image)
not increase the size for Virtualbox.  There are a couple of ways
that you can do this.  I haven't checked the VirtualBox Forums lately,
and you may want to start your search there, but this old posting on the
Ubuntu Forums will assist you.  Be sure to have a look at the Manual for
VirtualBox as I'm sure it has information that applies.  I don't remember
how I started the process.......It's been too long.....

[http://ubuntuforums.org/showthread.php?t=723219&highlight=vdi](http://ubuntuforums.org/showthread.php?t=723219&highlight=vdi)

If you need more assistance post back.  I think you will have enough
information to get it done, assuming you can locate the VDI file in
the VirtualBox folder on your Desktop.  That will depend on which version
of VirtualBox you are running.  Use CNTL H to display all folders/files
that start with a . and then look for .Virtualbox, drilling down from there.
The latest Version uses a folder on your Desktop, if I remember
correctly.  (At least it does in Debian 6.0 Squeeze)

Post back with your method, and how it went.

Another thing you may want to consider is to build a Minimum version of
Windows with nlite to strip the BLOAT from your Minimal Version, giving
you more room on your VDI for the things you want to run.
[http://www.nliteos.com/nlite.html](http://www.nliteos.com/nlite.html)


Thanks.

lk

---

### Post by lkraemer on 2011-03-17
The VirtualBox site has lots better information nowdays.........

REF:
[http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi](http://www.virtualbox.org/manual/ch08.html#vboxmanage-modifyvdi)


lk

---

