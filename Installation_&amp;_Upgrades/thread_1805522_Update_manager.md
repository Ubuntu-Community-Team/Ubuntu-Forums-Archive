---
title: "Update manager"
date: 2011-07-16
forum: Installation &amp; Upgrades
---

### Post by Aerogate on 2011-07-16
Hey there,

for the last 2 days I have been getting this error when I run the update manager :-

Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net///ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas?

Mike

---

### Post by plucky on 2011-07-16
> **Aerogate said:**
> Hey there,

for the last 2 days I have been getting this error when I run the update manager :-

Failed to fetch [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net///ubuntu/dists/natty/main/binary-i386/Packages](http://ppa.launchpad.net///ubuntu/dists/natty/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.

Any ideas?

Mike

Remove the PPA in Software Sources as there isn't one for Natty.

See [Here](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu/dists/)

Good Luck

---

### Post by raja.genupula on 2011-07-16
sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update


execute it one by one ...
you will be fine .

---

### Post by Aerogate on 2011-07-16
> **raja.genupula said:**
> sudo rm -rf /var/lib/apt/lists/*
sudo apt-get update


execute it one by one ...
you will be fine .

Excellent, removed ppa's like plunky said, then ran the commands, thanks Raja.

All fine

---

### Post by raja.genupula on 2011-07-16
i am happy to here this , but do me a favor . please close the thread by marking it solved .

---

