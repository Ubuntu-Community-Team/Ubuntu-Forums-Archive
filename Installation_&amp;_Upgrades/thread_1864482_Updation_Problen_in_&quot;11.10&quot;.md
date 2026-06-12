---
title: "Updation Problen in &quot;11.10&quot;"
date: 2011-10-19
forum: Installation &amp; Upgrades
---

### Post by PratikDutta on 2011-10-19
W:Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/bisigi/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by Rasa1111 on 2011-10-19
They apparently don;t work for 11.10 yet..
or no longer work at all..
you're links are 404'd. 

But,
If you go into your software sources and remove those two PPA's (bisigi and tualatrix)
Then do a sudo apt-get update, You should stop getting those errors.

good luck.

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remo...e-404-not.html](http://www.upubuntu.com/2011/07/remo...e-404-not.html)

---

