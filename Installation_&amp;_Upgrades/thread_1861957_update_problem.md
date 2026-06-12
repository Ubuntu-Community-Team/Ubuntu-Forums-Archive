---
title: "update problem"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by hhall on 2011-10-16
Hey,

Occasionally, but not always, my system fails to update properly. Usually, it seems to catch on downloading the last (of a total 75) packages, giving me this message:

Failed to fetch [http://deb.playonlinux.com/dists/hardy/main/binary-i386/Packages.gz](http://deb.playonlinux.com/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

Any idea what I should do about this?

---

### Post by ezramorris on 2011-10-16
> **hhall said:**
> Failed to fetch [http://deb.playonlinux.com/dists/hardy/main/binary-i386/Packages.gz](http://deb.playonlinux.com/dists/hardy/main/binary-i386/Packages.gz)  404  Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

It looks like it can't access the playonlinux repository. This is probably an issue on their side rather than yours. You can always check manually to see if it can be accessed by browsing to [http://deb.playonlinux.com/dists/hardy/main/binary-i386/](http://deb.playonlinux.com/dists/hardy/main/binary-i386/) in a web browser.

Ezra.

---

### Post by hhall on 2011-10-17
That appears to be the problem. I get a dead link for that address. Maybe best if I just dump playonlinux?

---

### Post by ezramorris on 2011-10-17
> **hhall said:**
> That appears to be the problem. I get a dead link for that address. Maybe best if I just dump playonlinux?

The other stuff should work even though it can't use that source?

---

### Post by mhgsys on 2011-10-17
Ubuntu 8.04's  (Hardy Heron) support ended on 12 May 2011 for desktops and will end in April 2013 for servers.


[http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)
also  Hardy is not on playonlinux anymore.
see;
 [http://deb.playonlinux.com/dists/](http://deb.playonlinux.com/dists/)

---

### Post by hhall on 2011-10-18
No, for some reason the entire process stalls. I'm on 10.04 (lucid, not hardy).

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

