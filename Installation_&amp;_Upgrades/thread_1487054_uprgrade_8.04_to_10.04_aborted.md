---
title: "uprgrade 8.04 to 10.04 aborted"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by Randy Schilling on 2010-05-18
I tried to upgrade from ubuntu 8.04 to 10.04.  The process terminated with the following message: "The upgrade is now aborted.  Your system could be in an unstable state.  A recovery will run now (dpkg --configure -a)".  
Then I tried to boot to my ubuntu disk. The grub boot loader showed several options, several version 10.04 kernels (no 8.04 kernels) and corresponding recovery options.  I tried a normal boot and it locked up in the first screen following the boot 
loader.  I did not try a recovery option.  Instead, I selected the
Windows option from the grub menu; this so I could could get this message off ASAP.  
 
I am in dire need of help.  I am a linux novice but I was doing very well learning about ubuntu and linux from the book by Kier Thomas.  I worked through almost all 700 or so pages and now I wish I had never tried this upgrade. 
 
I am running a pentium D cpu at 3ghz and 5gb ram.  It has two 150gb hard disks, one I call my ubuntu side, the other my windows side.  
 
I decided to learn linux at my son's behest.  After a virus infection and costly recovery, my windows side has not been the same.  It is disgustingly slow and it continues to slow down.  All I did was click on a picture of Rihanna and kaboom, infected!
 
Back to the upgrade. The upgrade was interrupted by messages of the form "Sorry, the packgage "x" failed to instal or upgrade" where 
x=gwibber2.30.0.1-0ubuntu1, 
libimobiledevice00.9.7-1ubuntu1, 
evolution-couchdb0.4.5-0ubuntu1, 
rtkit, 
libgpod40.7.93-0ubuntu1, 
python-desktopcouch-records0.6.4-0ubuntu3, 
libgpod-common0.7.93-0ubuntu1,
rhythmbox-plugins0.12.8-0ubuntu4, 
couchdb-bin, 
python-speechd0.6.8~unofficial~N2-0ubuntu3, 
nVidia-gix-new, 
python-desktopcouch0.6.4-ubuntu3, 
gvfs-backends1.6.0+git20100414-0ubuntu1, 
gwibber-service2.30.0.1-0ubuntu1,
rhythymbox-ubuntuone-music-store0.0.9-0ubuntu1, 
gnome-orca-2.30.0ubuntu3, 
desktopcouch0.6.4-0ubuntu3, 
speech-dispatcher.
 
What do I do from here?  Install 8.04 or 9.04 or 10.04 from scratch?  
Can I get back up and running with ubuntu without loosing the important documents on my ubuntu side?
 
Any help will be most graciously appreciated.  
Regards - Randy ([EMAIL="rchilling@comcast.net"]rchilling@comcast.net[/EMAIL])

---

### Post by zvacet on 2010-05-18
Boot in recovery mode and type

```
dpkg --configure -a
```

---

