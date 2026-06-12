---
title: "synaptic broken after a vmware adventure"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by philipgm on 2006-06-20
I recently tried installing vmplayer - why I did this is lost in a haze since I already had vmserver running! Anyway, the download and install from the repos, using synaptic, fell over and  then vmware server stopped working. At this point I decided to uninstall everything and reinstall vmserver. This seemed like a straightforward approach but at some point the vmplayer package has become "very badly corrupted". 

Using synaptic to uninstall always fails with the advice to run dpkg --configure -a just before synaptic dies. I run that command, restart synaptic, and the package is still there. This by itself wouldn't bother me, but now it seems to be affecting installation or reinstallation of other applications. Re-installing is not such an easy option as I use this machine for all my work and moving stuff won't be easy.

EDIT: I mean reinstalling Ubuntu

It seems that the problem is corruption of the package database so I'd like some help to recover that database if anyone knows a method;

TIA

Phil

---

### Post by siepo on 2006-06-20
You could try to type in a terminal:

sudo dpkg --purge vmplayer

Synaptic uses dpkg in the background. Dpkg keeps working even if something is not quite right with your installation.

---

### Post by philipgm on 2006-06-20
Hi siepo,

That gets me

sudo dpkg --purge vmware-player
dpkg: error processing vmware-player (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 vmware-player

But I know that a reinstall will fail - because it always does. 

Thanks for the idea though.

---

### Post by philipgm on 2006-06-20
OK, fixed it.

Not really a recommended approach but...

Delete everything on the disk that a file search can find. EDIT: i.e. search for vmware

Restart synaptic and re-install vmware-player

Then remove vmware-player - because I only set this up to run Internet Explorer in a moment of weakness. My machine is now a nice ubuntu install. Every time I go near something to do with microsoft my machine breaks, when will I learn...

---

### Post by apoclypse on 2006-06-22
I ahve the same exact problem. I'll give this a try.

---

### Post by philipgm on 2006-06-22
Any luck?

---

