---
title: "Failed to download Repository information (Ubuntu 12.04)"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by jamo4ever on 2012-05-20
Any help would be appreciated here, my first ever issue with Ubuntu since 10.10.I regularly update my system, I'm running Ubuntu 12.04, and now have a red triangle in the top right corner of screen beside my battery gauge, when I click it it says "The update information is outdated", when I check for new updates i get the message "Failed to download repository information, check internet connection"
Under details it says "W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/binary-amd64/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/binary-amd64/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead."

Anybody know what is wrong and how to fix it, greatly appretiated

---

### Post by arpanaut on 2012-05-20
There are no packages in that PPA for Precise. See: [http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/](http://ppa.launchpad.net/ilap/lwp/ubuntu/dists/)

You can either comment "#" those lines in your sources.list or change precise to oneiric in /etc/apt/sources.list.d 
 This can also be done from Software Sources app from software center or synaptic.

I don't know what that PPA is for so I don't know if the oneiric packages will work right or not.
You may want to do some investigation before you activate the oneiric packages.

---

### Post by jamo4ever on 2012-05-20
Thank you very much, i'll give them a try

---

