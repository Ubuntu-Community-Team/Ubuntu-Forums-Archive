---
title: "package crashing apt-get"
date: 2014-02-09
forum: Installation &amp; Upgrades
---

### Post by joenco2 on 2014-02-09
Hi, i'm trying to install [http://www.cabrio-fe.org/](http://www.cabrio-fe.org/) on my lubuntu 13.10.
I tried to install by .deb package but i get a dependence error, so i go to launchpad and downloaded libavcodec52 and i tried to install this one but it crashed. And now i can't install anything =(.

```
root@kali:/# sudo apt-get install -fReading package lists...
Building dependency tree...
Reading state information...
E: The package libavcodec52 needs to be reinstalled, but I can't find an archive for it.
root@kali:/# 



```

can someone help me to fix it and to install cabriofe?

thanks

---

### Post by FulciLives on 2014-02-27
I had Synaptic crash while it was installing some software and after that nothing else worked. What I mean is Synaptic wouldn't load, the Software Store wouldn't load, the Software Updater wouldn't load and even apt-get install <whatever> wouldn't work.'s 

So I jumped into Ubuntu's IRC channel and someone told me to do this:

```
sudo dpkg --configure -a
```
```
sudo apt-get -f install
```

I have no idea what the first line does but I was told to type both and that the second line will fix interrupted installs.

It worked for me! :)

---

