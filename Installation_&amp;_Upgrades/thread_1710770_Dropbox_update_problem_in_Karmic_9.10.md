---
title: "Dropbox update problem in Karmic 9.10"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by lylex on 2011-03-20
I've had a problem doing updates to Ubuntu 9.10 Karmic for months.  I'd like to upgrade, but figure I should solve the update issue first.

The output of "apt-get update" is:
------------
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release.gpg
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Translation-en_US
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic Release
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Packages
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Sources
Ign [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Sources
Hit [http://linux.dropbox.com](http://linux.dropbox.com) karmic/main Sources
Fetched 198B in 10s (19B/s)
Reading package lists... Done
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release: The following signatures were invalid: BADSIG 54422A4B98AB5139 Oracle Corporation (VirtualBox archive signing key) <info@virtualbox.org>
W: Failed to fetch [http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release](http://download.virtualbox.org/virtualbox/debian/dists/karmic/Release)
------------

Any advice is appreciated, as it's driving me nuts. 8-)

Thanks...Lyle

---

### Post by oracle2b on 2011-03-20
You can just remove the virtualbox source repo from "Software Sources".

[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu") Go to "Removing & Disabling Repositories".

---

### Post by mörgæs on 2011-03-20
9.10 is running out of support very soon, so you shouldn't struggle with it. Better is to wipe the drive and do a clean install of 10.04 or 10.10.

---

