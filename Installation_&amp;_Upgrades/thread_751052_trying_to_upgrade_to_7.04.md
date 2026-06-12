---
title: "trying to upgrade to 7.04"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by pennyminstrel on 2008-04-10
I'm trying to upgrade to Ubuntu 7.04 using the update manager, but its failing at the first step with this message:

'A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release) Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)'

I'm absolutely stumped - I don't have wine installed at the moment and there's no problem with the network.

Anyone got any suggestions?

Penny

---

### Post by dje on 2008-04-10
Try this:
```
sudo gedit /etc/apt/sources.list
```
Then find the line 'deb [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)' and put a hash in front of it like this:
```
#deb http://wine.budgetdedicated.com/apt/dists/edgy/Release
```
Then save and close the file, finally run:
```
sudo apt-get update
```
Now try and do the upgrade

hope that helps,
dje

---

### Post by pennyminstrel on 2008-04-10
Thanks dje,

There wasn't a wine line in the sources list, but you put me on the right track. In Software Sources under Administration I found that the wine repositories were ticked there, got rid of the ticks and all went well.

Thanks again.

penny

---

### Post by dje on 2008-04-10
No problem, glad you got it sorted

dje

---

