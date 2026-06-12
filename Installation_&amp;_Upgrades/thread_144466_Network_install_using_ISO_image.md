---
title: "Network install using ISO image"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by aixguy on 2006-03-14
I am trying to develope a method of loading Ubuntu server on entreprise class Intel boxes like I do AIX using NIM.  So far, I have managed to set up a DHCP server and boot using the PXE network install and the server loads using the internet to pull files down.  
I would like to load from an ISO file on a local NFS mount rather than our 100 KBS internet tubing..
I do not want to utilize the CDROM or floopy drive since I am a remote emplyee and need to be able to work unassisted.  
I am also not the fimiliar with Linux, so please keep that in mind when you respond.  
Thanks in advance,
Doug

---

### Post by aixguy on 2006-03-14
bump

---

### Post by John.Michael.Kane on 2006-03-14
[http://www.ubuntuforums.org/showthread.php?t=28948](http://www.ubuntuforums.org/showthread.php?t=28948)
[http://marc.herbert.free.fr/linux/win2linstall.html](http://marc.herbert.free.fr/linux/win2linstall.html)

---

### Post by aixguy on 2006-04-05
Those links were of some help, however, I want to boot from pxelinux.0 and load from a mounted ios file. 
In other worked.. Imake a nice standard install with just the packages I want, back it up to nfs mounted storage using mondo, then when I need a new server or want to restore this one.. I can load it without any cd or even being in the building.. same stuff I have been doing in AIX for years..

---

