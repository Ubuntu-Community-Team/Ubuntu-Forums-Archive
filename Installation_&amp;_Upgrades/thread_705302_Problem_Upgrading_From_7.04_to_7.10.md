---
title: "Problem Upgrading From 7.04 to 7.10"
date: 2008-02-23
forum: Installation &amp; Upgrades
---

### Post by Davehogs on 2008-02-23
When I try following the posted upgrade procedure using the Upgrade Manager all goes well until a window pops up and says:


[SIZE="4"]Error during update[/SIZE]

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/edgy/non-free/binary-i386/Packages.gz) 302 Found

I cannot believe that I am the only one this is happening to, Can someone give me a solution ?

---

### Post by forestpixie on 2008-02-23
can you post your sources list

```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/medibuntu.list
```

Edit - in fact that edgy site goes to the medibunut main site now, try editing the file it's in - either /etc/apt/sources.list or /etc/apt/sources.list.d/medibuntu.list

open them with gedit if you're using ubuntu 

```
gksudo gedit *fileto edit*
```

find the lines that are causing the error and put a # in front, save the file and do 

```
sudo apt-get update
```

---

