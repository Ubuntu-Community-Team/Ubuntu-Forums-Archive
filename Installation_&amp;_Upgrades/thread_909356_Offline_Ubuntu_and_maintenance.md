---
title: "Offline Ubuntu and maintenance"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by ashtangiman on 2008-09-03
I am thinking to buy a new dell (530N) with Ubuntu to use as a home media server/ PVR (Myth).  I don't have the internet at home though, and wonder how feasible it is to maintain Ubuntu, and to add packages etc. without an internet connection.  I could take the machine to my office for the initial setup (for any packages that might not be in the included distro, 8.04).  But beyond that do the installation managers allow for checking dependencies, and generating scripts or something that can be used to download libraries etc. from a different (Windows or OSX) machine?

Any insight into this is greatly appreciated.  Thanks, Paul

---

### Post by Partyboi2 on 2008-09-03
It does pay to have a internet connection when using ubuntu, but there are ways to install packages and there dependencies offline. There is the [[COLOR=Blue]synaptic package manager downloaded script[/COLOR] ]("https://help.ubuntu.com/community/Synaptic/PackageDownloadScript")
There is also a new project under way  called [[COLOR=Blue]keryx[/COLOR]]("http://keryx.betaserver.org/") which will allow you to update your machine using usb.

---

### Post by _khAttAm_ on 2009-01-28
try [http://www.offlineubuntu.co.cc](http://www.offlineubuntu.co.cc)

---

### Post by talktorishav on 2010-01-07
You can easily do this using Synaptic Package Manager. The other computer having internet can be anything. Alternatively you can also use Linux live CD in the computer having internet. In case its Windows you need to have a download manager.

The detailed steps are here: 
[http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html](http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html)

Or you can also use tools like:
[http://www.webupd8.org/2009/12/sushi-huh-easily-download-packages-for.html](http://www.webupd8.org/2009/12/sushi-huh-easily-download-packages-for.html)

The choice is yours! Enjoy :P

---

### Post by Bartender on 2010-01-08
There's a big difference between having a slow connection at home and NO connection.  This blog

[http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html](http://techspalace.blogspot.com/2009/04/offline-update-ubuntu.html)

is overly simplified and does not work as described.  You'll have to trust me on this, because I've been using Synaptic's Download Script heavily this last week.

We've got dial-up at home.  It took 15 minutes, but Synaptic was able to Reload all packages that needed to be updated.  Click Apply, then go to File>Generate package download script, save the file to a thumbdrive, go find some broadband with a Linux PC that has wget installed, bring it back home, it's a fairly painless process.

But a PC at home that has NO internet connection cannot tell you what it needs, so it's more complicated to create a download script.  I've seen several explanations but haven't tried any of them yet.

Also, the blog is incorrect about simply marking packages you want to install.  I generated package download scripts for four applications; hugin, hplip, ccsm, and Sunbird.  The script collected all the necessary packages for Sunbird and ccsm, but not hugin or hplip.

We were discussing this in the last several pages of this [thread]("http://ubuntuforums.org/showthread.php?t=1238954").

For some other ideas: [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

