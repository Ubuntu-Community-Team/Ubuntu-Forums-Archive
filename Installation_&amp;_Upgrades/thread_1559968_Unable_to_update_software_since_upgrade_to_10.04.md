---
title: "Unable to update software since upgrade to 10.04"
date: 2010-08-24
forum: Installation &amp; Upgrades
---

### Post by dai_bach on 2010-08-24
Three weeks ago I upgraded to 10.04 from 9.10.  However, since then I have been unable to update/upgrade my system software - i.e. doing both ```
sudo apt-get update
``` and the Update Manager fail.  I receive the messages along the following lines:
```
Err http://fr.archive.ubuntu.com lucid-security/main Sources
  Unable to connect to fr.archive.ubuntu.com:http: 
```

I've tried changing my mirror to Main, US, and any number of the servers in France and the UK but nothing changes.  My internet connection doesn't appear to be affected so what can be the matter?

I'm running the 64 bit version of lucid and have the following lines in my /etc/apt/sources.list
```
###### Ubuntu Main Repos
deb http://fr.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 
deb-src http://fr.archive.ubuntu.com/ubuntu/ lucid main restricted universe multiverse 

###### Ubuntu Update Repos
deb http://fr.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb http://fr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 
deb-src http://fr.archive.ubuntu.com/ubuntu/ lucid-security main restricted universe multiverse 
deb-src http://fr.archive.ubuntu.com/ubuntu/ lucid-updates main restricted universe multiverse 

```

---

