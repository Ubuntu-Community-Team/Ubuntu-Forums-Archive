---
title: "Gutsy Lamp server install problems"
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by MrLewDog on 2007-12-12
I am trying to install Gutsy Lamp Server on an old box with 40 gig hard drive 1 gig processer and 256 megs of memory. I know its old, but i am just using it for testing and development.

I follow the instruction on the CD every thing is going good until I restart.  It seems to hang on the "Running Local Scripts " .  I can press enter and log into the server, but when I try to change the configuration files using "sudo vi" it shows up as empty.  

Any Ideas.  Still new to Linux, I would appreciate any help.

Thanks

---

### Post by louieb on 2007-12-12
I guess you did a server install. Thats normal to have to press enter to get the logon prompt.

Don't know why sudo vi whatever.file brings up an empty file. 
Try ```
sudo nano /etc/apt/sources.list
```While your in there might as well enable the other repositories. Instructions are in the file.
then run 
```
sudo apt-get update
sudo apt-get safe-upgrade 
```safe-upgrade is for gutsy only all others use dist-upgrade.
a nice command line file manager is mc (midnight commander)
```
sudo apt-get install mc
```Let us know how it goes.

---

