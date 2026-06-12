---
title: "Kubuntu install over Server 6.10"
date: 2006-12-06
forum: Installation &amp; Upgrades
---

### Post by Kornbukler on 2006-12-06
I'm trying to set up what is essentially a server with RAID1 and EVMS, but it needs to be accessed occasionally by users who are not happy with the command line (!?!).

I'd have liked to achieve the results by simply installing kubuntu but that does not seem to provide for the possibility (despite what some documentation seems to imply), perhaps I downloaded the wrong image.

I did an install of edgy server and that is all running happily with the required filesystem setup, I'm now trying to add the kubuntu desktop with apt-get and getting into trouble.

The FAQ says run 'apt-get install kubuntu-desktop'. This is downloading new packages OK, but it is also demanding the CD labelled `Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)' and won't recognise the CD I have which is the latest downloadable version.

Ideas please.  I'm assuming that the relevant information is in README.diskdefines and have tried burning a new copy with the correct value of DISKNAME without success.

---

### Post by eye208 on 2006-12-06
Assuming the CD gets mounted to /media/cdrom0 as usual, just edit /etc/apt/sources.list, comment out the existing cdrom: line, then add:

deb file:/media/cdrom0 edgy main restricted

Run sudo apt-get update, then sudo apt-get install kubuntu-desktop. The name of the CD won't matter any more as long as it is mounted to /media/cdrom0.

---

### Post by Kornbukler on 2006-12-06
> **eye208 said:**
> Assuming the CD gets mounted to /media/cdrom0 as usual, just edit /etc/apt/sources.list, comment out the existing cdrom: line, then add:

deb file:/media/cdrom0 edgy main restricted

Run sudo apt-get update, then sudo apt-get install kubuntu-desktop. The name of the CD won't matter any more as long as it is mounted to /media/cdrom0.


OK, that was it.  Thank you.

---

