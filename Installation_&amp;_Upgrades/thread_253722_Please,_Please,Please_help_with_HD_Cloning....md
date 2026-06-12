---
title: "Please, Please,Please help with HD Cloning..."
date: 2006-09-08
forum: Installation &amp; Upgrades
---

### Post by knichel on 2006-09-08
I have a lab with several Identical computers.  I installed and configured 1 computer and set everything just the way I wanted.  My plan was to clone it to the rest of the HD's using Norton Ghost and then change the hostname and ethernet adapter info and start using them.  The clone seemed to go ok (fast if nothing else).  When I installed the hard drives into the other computers and booted them up all seemed fine.  I started to change the hostname and ip info, but it didn't work.  The hostname would not change.  It kept reverting back to the name of the source drive.  I ended up su'ing and changin it in /etc/hosts and /etc/hostname. This seemed to work on a few of them but not on others.  The prompt in terminal still shows admin@WS6 (which is the hostname of the source drive I used for cloning) even though /etc/hostname shows WS3 and similar is true for /etc/hosts.

The other major problem I am having is that on a few of the computers, I cannot seem to get the network to ... well, work.  I have Linksys wireless routers and nic's.  I have the settings set identically and the network is working on one machine but not another.  I have checked the routing table and the routes are identical and the ip config on the cards is identical.  

Another strange (not life threatening) problem is that the wireless adapters on the source drive were labeled ra0 and ra1.  When I cloned the drive, then adapters are labeled ra2 and ra3.  What is up with that?

Many peopel on #linuxhelp and #ubuntu have given suggestions about which program to use to clone.  I have used ghost in the past (last year) and it worked fine.  I was able to change what I needed to change and all worked ok.

I read about several programs (dd, g4u, g4l, and others), but have had some glitch with them as well.  My HD's are SATA and that seems to have caused me some problems itself (some programs not recognizing the drive when I boot from the cd.  Can't clone a drive I can't see.)

Please, please, please somebody help me.  I need to get my classroom up and running asap.

--
Mike

---

