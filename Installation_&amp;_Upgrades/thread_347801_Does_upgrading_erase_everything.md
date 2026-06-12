---
title: "Does upgrading erase everything?"
date: 2007-01-27
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2007-01-27
I'm thinking of upgrading from Dapper to Edgy, but I wanted to know if all of my app. launchers and settings and saved stuff will be transferred over if I did. I don't want to have to go and re-install everything and redo all of my personal settings and stuff, is there a way to copy them over to Edgy (if it's not done automatically).

Also, if anyone could give some general feedback (like whether it's worth upgrading) about Edgy, that'd be great too.

---

### Post by GrammatonCleric on 2007-01-27
I don't believe so.  Before you do a good rule of thumb make a good backup of your system first.  Even better image your system using G4U ([http://fbim.fh-regensburg.de/~feyrer/g4u/](http://fbim.fh-regensburg.de/~feyrer/g4u/)) or something comparable.  I should warn you G4U can take a long time to create a image but restoring is pretty fast.  I've been using Edge for awhile now (Servers and Workstations) had a few problems at first (video drivers) otherwise no issues.

-GC

---

### Post by rainwalker on 2007-01-27
Can I back it up to a Windows workstation over a network? Or will that take too long?

---

### Post by GrammatonCleric on 2007-01-27
Yes, you can.   G4U uses FTP as it creates the image.  You can download [FileZilla's FTP server]("http://sourceforge.net/project/showfiles.php?group_id=21558") to transfer the G4U image to the Windows box.   Be sure to setup a user/password as well as specify a directory for that user before you try to use G4U.  G4U's boot disk requires a DHCP server to get an IP.  Do you have a router or something running DHCP on your network? 

When you are ready boot from the G4U boot disk which can be downloaded from... 

[http://fbim.fh-regensburg.de/~feyrer/g4u/]("http://fbim.fh-regensburg.de/%7Efeyrer/g4u/")

If all goes well from the command prompt type something like...

uploaddisk username@192.168.0.100 the-name-of-your-image.gz

(substitute the ip address of the system running the FTP server)
You should be prompted for the password you set for the user in FileZilla Server.  

Again the G4U image creation can take a long time. Be patient.

-GC

---

### Post by rainwalker on 2007-01-27
I honestly have no idea, my dad would know. I'm not really familiar with FTP and DHCP stuff, but I'll see what I can do.

Thanks  :D

---

