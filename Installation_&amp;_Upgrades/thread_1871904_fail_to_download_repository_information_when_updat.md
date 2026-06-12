---
title: "fail to download repository information when updating"
date: 2011-10-29
forum: Installation &amp; Upgrades
---

### Post by Cozze on 2011-10-29
hi,

I've been reading the answers to similar problems but I just don't get what the answers mean ... I am absolutely not into computers .... i just like the open source idea

So, I've upgraded to 11.10 successfully but when I want to run an update I get following error message:

failed to download repository information, check your internet connection.
W:Failed to fetch [http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

, W:Failed to fetch [http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

, E:Some index files failed to download. They have been ignored, or old ones used instead.

There is nothing wrong with my internet connection. so can you please describe in simple wording how to solve this?

Tx, Cozze

---

### Post by Frogs Hair on 2011-10-29
I just had the same problem with a different source last night. I waited until today and re-entered the PPA source and ran the following in the terminal . ```
sudo apt-get update
```

I had no problem connecting to the source today. If the PPA is compatible with 11.10 it is probibly just a connection glitch with that source . If it persists check the launch pad page for the PPA to see that it is still compatible with 11.10 .

If you remove the source from the source list the software will no longer update .

---

### Post by oldos2er on 2011-10-29
There is a typo in "http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/source/Sources", it should be "http://ppa.launchpad.net/tiheum/equino[COLOR="Red"]x[/COLOR]/ubuntu/dists/oneiric/main/source/Sources"
Note the letter in red. You will need to find the PPA source list in /etc/apt/sources.list.d/ and edit it accordingly.

---

### Post by raja.genupula on 2011-10-29
> **oldos2er said:**
> There is a typo in "http://ppa.launchpad.net/tiheum/equino/ubuntu/dists/oneiric/main/source/Sources", it should be "http://ppa.launchpad.net/tiheum/equino[COLOR="Red"]x[/COLOR]/ubuntu/dists/oneiric/main/source/Sources"
Note the letter in red. You will need to find the PPA source list in /etc/apt/sources.list.d/ and edit it accordingly.
+1
1.Change your server from update manager->settings and then try again.

if you again got the same error then 

2.update manager-->settings-->other software

uncheck the checkbox's of those error PPA's

all the best.

---

### Post by Cozze on 2011-11-01
ok, tx I'll try that.

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

---

