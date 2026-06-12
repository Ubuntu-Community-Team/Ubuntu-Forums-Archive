---
title: "Add Applications error"
date: 2005-11-03
forum: Installation &amp; Upgrades
---

### Post by Terrycymru on 2005-11-03
I've just used System>Administration>Add Applications to install Liferea. It appears to have installed OK but during the process I got this error message:

[B]W:Couldn't stat source package list http:gb.archive.ubuntu.com/breezy-updates/ Main Packages (/var/lib/apt/lists/
gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)[/B]

What does this mean? I assume gb.archive.ubuntu.com is a server with gb localisation.

---

### Post by Xian on 2005-11-03
Do you have multiple copies of the same repositories in your sources.list?
It could also be that the server is having a problem.

If your sources.list is okay try changing the mirror.

---

### Post by aysiu on 2005-11-03
Sounds like a sources.list error. Follow these instructions to get an updated sources.list:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

---

### Post by Terrycymru on 2005-11-04
Thanks for your replies. Looks like it was a server error. I've added Thunderbird this morning without any error message but I'll check the sources list.

---

