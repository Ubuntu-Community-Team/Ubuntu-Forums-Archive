---
title: "apt-get update result in errors."
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2011-10-16
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
  404  Not Found
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) oneiric-updates/universe Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages
  404  Not Found



W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/ferramroberto/vlc/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by dino99 on 2011-10-16
do you really understand what you are doing ?

mixing i386 & amd64 repo is not a clever idea. Adding ppa often add deb-scr but they dont exist, so wake up :)

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

### Post by Starfleet on 2011-11-10
hoboy, common problem on a new release. I too had this problem with 11.10 and many others have too. It's just that the author of those packages hasn't yet made them available in the launchpad repo yet. They will come eventually I'm sure. There are workarounds if you search this forum.

dino, bit harsh with our friend I think! If installing from a 'to do list' as many people do, then unless you edit out the command for the irrelevant repo you will of course load it. Many are not sure how to do that or don't see it as a problem. It makes no difference whatsoever to the installation as the correct software will still be loaded. The odd error message is of no real consequence and is easy to deal with if you want to remove it. :)

---

