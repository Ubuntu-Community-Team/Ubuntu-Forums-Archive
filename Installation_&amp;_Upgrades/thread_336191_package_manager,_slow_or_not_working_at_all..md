---
title: "package manager, slow or not working at all."
date: 2007-01-11
forum: Installation &amp; Upgrades
---

### Post by arewhyainn on 2007-01-11
I've been trying to install packages from the system update and synaptic package manager, as well as "apt-get install" I've used these in the past so I know how to use them. One of the biggest problems I have is I can't download the repository indexes. this is the error I get...

> 
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/main/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)


I can go to the url that it gives me and download the index but where would I go about placing it. I was able to download the needed update but it was very slow =< 10Kb/s. and yes my internet connection is faster then that.

and I'm using 6.10

---

### Post by taurus on 2007-01-11
Edit /etc/apt/sources.list and remove the "**us.**" from your repos.  That should speed up the downloading process...

Applications -> Accessories -> Terminal
```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by arewhyainn on 2007-01-11
thank you very much :)

---

### Post by taurus on 2007-01-11
You're welcome.

---

