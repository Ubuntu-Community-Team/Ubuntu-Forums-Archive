---
title: "program error after upgrading to 9.10 Ubuntu"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by elviselviselvis on 2009-12-31
Could someone look this over and give me the details on how i remove the package or program that did not recomplie correctly and doesnt behave right.
Its called Novacom  i was using it when testing some tethering with my palm pre, but as you can see in the terminal output below everytime i install a new package i get the same error about trying to recompile novacom...

Im new to Linux but really liking not being on windows any more... :)

Thanks

<<><>< terminal output below ><><><
Unpacking kooldock (from .../kooldock_0.3-1ubuntu3_i386.deb) ...
Processing triggers for man-db ...
Setting up palm-novacom (0.3-svn177284-hud9) ...
stop: Unknown job: novacomd
stop: Unknown job: palm-novacomd
start: Unknown job: palm-novacomd
dpkg: error processing palm-novacom (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up kooldock (0.3-1ubuntu3) ...
Errors were encountered while processing:
 palm-novacom
E: Sub-process /usr/bin/dpkg returned an error code (1)
sam@sam-laptop:~$

---

### Post by elviselviselvis on 2010-01-02
I stumbled onto the program called Synaptic Package manager, which allowed me to highlight the driver/package and remove from the installation.

Pretty simple, i just didnt know where to look....

---

### Post by jonest1 on 2010-01-02
I had this one as well as I just had to re-install webos quick install and ran into this one.  Basically, the post install script in the package is broken.  It still installs okay, but the novacomd service is not started automatically.

A couple notes, when using webos quick install, I had to open another terminal and run novacomd with sudo to get the pre to be recognized.

Due to the problem with the package, you will continue to get the notification with each apt-get command regardless of whether or not it has anything to do with the novacom package.

You can remove it through Synaptic or I suppose the following will also work.
```
sudo apt-get remove palm-novacom
```

You would then have to re-install it each time you wanted to connect your pre.

---

### Post by elviselviselvis on 2010-01-02
Thanks Jonesst1,
Will try that also....

cheers

---

### Post by elviselviselvis on 2010-01-02
I ran that remove command, but look like the Package manager did the uninstall...


><><><terminal output><><><><
sam@sam-laptop:~$ sudo apt-get remove palm-novacom
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package palm-novacom
sam@sam-laptop:~$

---

