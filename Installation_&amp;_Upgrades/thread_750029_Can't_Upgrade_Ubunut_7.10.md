---
title: "Can't Upgrade Ubunut 7.10"
date: 2008-04-09
forum: Installation &amp; Upgrades
---

### Post by mthalis on 2008-04-09
When i reload Synaptic Package Manager It give following error how can i resolve it.

[http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:](http://archive.ubuntu.com/ubuntu/dists/gutsy/Release:) Unable to find expected entry  main'/binary-i386/Packages in Meta-index file (malformed Release file?)

---

### Post by Partyboi2 on 2008-04-09
Can you open a terminal and type
```
cat /etc/apt/sources.list
``` then post back the results.

---

### Post by mthalis on 2008-04-09
# deb [http://192.248.16.96:9999/japt-proxy/ubuntu](http://192.248.16.96:9999/japt-proxy/ubuntu) gutsy main restricted multiverse universe
# deb [http://192.248.16.96:9999/japt-proxy/ubuntu](http://192.248.16.96:9999/japt-proxy/ubuntu) gutsy-updates main restricted multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main' main universe restricted multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb file:///home/ucsc/dinesh-repo binary/

---

### Post by Partyboi2 on 2008-04-09
try replacing your sources.list with a new one.
open a terminal
backup your current one.
```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak
```then open the sources.list
```
gksudo gedit /etc/apt/sources.list
```delete the contents and replace with this one
> ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
 ## Uncomment the following two lines to fetch major bug fix updates produced 
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-updates main restricted 
 ## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted 
 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy multiverse 
 deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse 
 deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
 then save the file
and in the terminal
```
sudo apt-get update
```

---

### Post by mthalis on 2008-04-09
Thanks lot its work.

---

### Post by Tomatz on 2008-04-09
> **mthalis said:**
> # deb [http://192.248.16.96:9999/japt-proxy/ubuntu](http://192.248.16.96:9999/japt-proxy/ubuntu) gutsy main restricted multiverse universe
# deb [http://192.248.16.96:9999/japt-proxy/ubuntu](http://192.248.16.96:9999/japt-proxy/ubuntu) gutsy-updates main restricted multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main' main universe restricted multiverse
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb file:///home/ucsc/dinesh-repo binary/
   

I think it is the **'** that is the problem ;)

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main**' **main universe restricted

---

