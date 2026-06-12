---
title: "Server Install"
date: 2006-09-15
forum: Installation &amp; Upgrades
---

### Post by jsolomon on 2006-09-15
I would like to set up a very basic FTP server.  I have an old pc with an amd processor, 640 or so MB ram and 2 HD.  The primary drive is 10GB and the secondary is 20GB.  Two questions, the first is should I set up a LAMP server if the only thing I'll be running is just basic FTP.  The second question is what do you think is optimal HD wise when setting up this server.  Should I install the OS to the first drive and keep the second free like on a windows PC, or how should I go about partitioning.  Any help would be greatly appreciated.   THanks.

---

### Post by kidders on 2006-09-15
Hi there,

I think your first question answers itself, really :-P What would you need apache/php/mysql for if all you want is an FTP server?

The answer to your second question very much depends on how loaded (and how fast) your PC is. In general performance terms, there is something to be said for spreading your OS across a few physical devices, but if you're only ever going to be running one application (ie your FTP server), and your PC is old (so its I/O buses won't be terribly quick anyway), then there would be no difference, in my opinion.

I suppose you could consider mirroring your FTP repository over a couple of disks. If you're going to be serving a lot of data to a lot of users, it might boost their data rates.

---

