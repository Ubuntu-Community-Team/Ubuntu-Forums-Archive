---
title: "upgrading to 10.04 using a local network location"
date: 2010-05-10
forum: Installation &amp; Upgrades
---

### Post by flayme on 2010-05-10
Hi,
If I wanted to upgrade multiple computers to 10.04 using a location on my local network rather than burn my broadband download quota at 700mb per install, where would I go to get the files or archive containing the upgrade?
Thanks,
Peter

---

### Post by lechien73 on 2010-05-10
I've never tried it, but I presume you could use apt-mirror to create a mirror of the repository on your local network, and then just set "Software Sources" on each machine to point to the local mirror.

The information here: [http://apt-mirror.sourceforge.net/](http://apt-mirror.sourceforge.net/) as well as a bit of digging on the Internet should yield some instructions on how to set it up.

---

### Post by flayme on 2010-05-10
thanks lechien, but it is not that i just want to run a number of computers off a central server, but also may want to service computers with ubuntu on them.  You know, just like the service packs in windows, you can download the file and apply it to any number of pcs.  Download it once, and run it many times as needed, rather than upgrade over the internet each time and burn your broadband quota.  Just stick it in a folder on the server and log on to the server from a machine on the workbench and run the upgrade as needed.

So thanks again

cam on anh nhieu

---

