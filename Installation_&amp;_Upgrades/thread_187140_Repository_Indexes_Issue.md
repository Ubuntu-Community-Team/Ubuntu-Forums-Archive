---
title: "Repository Indexes Issue"
date: 2006-06-02
forum: Installation &amp; Upgrades
---

### Post by travelerthe on 2006-06-02
I am receiving the following error when starting the download for upgrading from Breezy to Dapper:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.


[http://theli.free.fr/packages/breezy/./Packages.gz:](http://theli.free.fr/packages/breezy/./Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Packages.gz:) 404 Not Found
[http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:](http://koti.mbnet.fi/~ots/ubuntu/breezy/Sources.gz:) 404 Not Found

Suggestions? I'm not sure what to try changing.

---

### Post by travelerthe on 2006-06-02
I think I solved my own problem by reading further into the forums.
Testing now.
Synaptic Package Manger/Repostiories/Uncheck the offending ones.

---

### Post by johnc4510 on 2006-06-02
I believe these are repositories that automatix put in the list when you had breezy. It is safe to delete them. To do that follow these commands:
Applications>Accessories>Terminal
sudo cp /etc/apt.sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list
Find the 3 lines above that were a problem and either delete them out or put a # in front of them. Save the file and close the window.
sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by travelerthe on 2006-06-02
Good to go on upgrade.
That got it.
Thank you for the assistance.

Now if only I could get JAVA to work with Firefox, but that's a problem for later.

---

