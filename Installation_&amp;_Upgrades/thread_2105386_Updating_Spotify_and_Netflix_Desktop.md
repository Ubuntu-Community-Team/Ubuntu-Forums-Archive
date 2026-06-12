---
title: "Updating Spotify and Netflix Desktop"
date: 2013-01-15
forum: Installation &amp; Upgrades
---

### Post by sks24 on 2013-01-15
12.04.1 LTS, 32 bit machine.  W/r/t repository.spotify.com and ehoover/compholio/ubuntu precise (Netflix)  I can't get past: "The action would require the installation of packages from not authenticated sources." 

Might this work?:
```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

I found it here: [http://askubuntu.com/questions/85641/how-do-i-deal-with-unauthenticated-sources-errors-in-the-software-center](http://askubuntu.com/questions/85641/how-do-i-deal-with-unauthenticated-sources-errors-in-the-software-center)

All "Software Sources" boxes are checked in settings.

Thanks in advance,
Scott

---

