---
title: "Adding extra repositories"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by ianc1 on 2011-05-15
[FONT=Verdana]I hope this is the correct part of the forum for this query.

When I first started using Linux (Ubuntu 9.10) when I wanted to use extra repositories I simply added the info to /etc/apt/sources.list and then got the key from the key server.

Now whenever I go to launchpad there are instructions to do the following:[/FONT]```
[FONT=Verdana]sudo add-apt-repository ppa:user/ppa-name[/FONT]
```[FONT=Verdana]This from memory created some extra directories and files in [/FONT][FONT=Verdana]/etc/apt/sources.list.

Whilst the auto downloading of the key is handy I prefer everything in sources.list particularly when it comes to upgrade time.  Is there any reason why I cannot continue to do this?

Thanks in advance for your replies.
[/FONT]

---

### Post by ajgreeny on 2011-05-15
You could just copy the entries in the various files in sources.list.d folder to your sources.list.

As an example here is my sources.list.d/medibuntu.list file:-
```
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ lucid free non-free #Medibuntu - Ubuntu 10.04 "lucid lynx"
# deb-src http://packages.medibuntu.org/ lucid free non-free #Medibuntu (source) - Ubuntu 10.04 "lucid lynx"
```
Just copy that to your sources.list and it should work exactly the same.  The **add-apt-repository** command is just a quick way to add it, but it puts them into these other sites in order to keep the original "clean" and make removal of the ppa repos easier.  If you make those changes it may stop **ppa-purge** working.

---

### Post by ianc1 on 2011-05-15
Thanks.  I see the point regarding ppa-purge which I had not yet come across but can understand it would be handy.

The problem I have with add-apt-repository is the effort required to go and find the info for all repositories I have put on the system - admittedly not much effort but it is more than opening the one file.  I suppose I could alias add-apt-repository with a short script to log then all in a separate file appending each new repository.

Thanks again.

---

### Post by ajgreeny on 2011-05-15
> **ianc1 said:**
> Thanks.  I see the point regarding ppa-purge which I had not yet come across but can understand it would be handy.

The problem I have with add-apt-repository is the effort required to go and find the info for all repositories I have put on the system - admittedly not much effort but it is more than opening the one file.  I suppose I could alias add-apt-repository with a short script to log then all in a separate file appending each new repository.

Thanks again.
But all of that repo information is in the one folder /etc/apt/sources.list.d, so to backup & get rid of those files; (they will be useless after an upgrade to new distro in any case), simply run ```
cat /etc/apt/sources.list.d/* > ppa.txt && sudo rm /etc/apt/sources.list.d/*
``` to make one txt file with all the data from those files, then remove them all.

You can  then ```
sudo apt-get update
``` to refresh.

---

