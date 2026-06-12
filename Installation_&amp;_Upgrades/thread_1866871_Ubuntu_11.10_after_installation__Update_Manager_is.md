---
title: "Ubuntu 11.10 after installation | Update Manager is not updating"
date: 2011-10-22
forum: Installation &amp; Upgrades
---

### Post by Rahuljaiswal on 2011-10-22
Hi,

I have successfully upgraded from Ubuntu 11.04 to Ubuntu 11.10. and it is working perfectly fine except that when ever i start Update Manager, it is giving me this error

W:Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found
, E:Some index files failed to download. They have been ignored, or old ones used instead.

My interned connection is working perfectly fine. I don't know how to fix it. 

Thanks & Regards
Rahul

---

### Post by zvacet on 2011-10-22
When I try those links I get same message,so it have to be something PPA related.Did you looked if PPA for 11.10 exist?

---

### Post by Old_Grey_Wolf on 2011-10-23
There is no pidgin development PPA repo for 11.10. Whatever version of pidgin that was in the PPA is probably the version 11.10 is using. Remove the PPA from update manager.

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

