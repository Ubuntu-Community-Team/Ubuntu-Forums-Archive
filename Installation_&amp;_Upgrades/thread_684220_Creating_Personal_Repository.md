---
title: "Creating Personal Repository"
date: 2008-01-31
forum: Installation &amp; Upgrades
---

### Post by neurostu on 2008-01-31
I am managing some custom software that is going to be under constant update and will be distributed onto several machines in my LAN. I am thinking about setting up a APT repo that will contain the latest version of my programs but I can't get it to work quite right: 

I have all my .DEB files in a folder named debs/  I tried the following:
```

acq@ubuntu:~/debs$ apt-ftparchive | gzip -9 > repo.gz
```
I then added the following line to the sources.list file
```
 deb file:///home/acq/debs/ gutsy repo 
```
When I run 
```
 sudo aptitude update 
```

Aptitude gives me an error saying File Not Found.

I don't know if I am doing this right please help!

---

### Post by bazzer on 2008-02-04
you could try apt-proxy? so you set one PC to be the 'master' and all the others to look to that one for their updates. If you update one of the PCs, the proxy grabs it,  and as a result all subsequent downloads are much quicker to the other PCs.

---

### Post by Seisen on 2008-02-04
Check this out 

[https://help.ubuntu.com/community/Repositories/Personal]("https://help.ubuntu.com/community/Repositories/Personal")

---

