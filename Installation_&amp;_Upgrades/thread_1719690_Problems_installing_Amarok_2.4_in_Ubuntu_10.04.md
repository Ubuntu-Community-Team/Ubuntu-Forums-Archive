---
title: "Problems installing Amarok 2.4 in Ubuntu 10.04"
date: 2011-04-02
forum: Installation &amp; Upgrades
---

### Post by shinkaide on 2011-04-02
I recently downgraded to Ubuntu 10.04 because of some problems with 10.10 (and I'm not very keen on 11.04, but I digress). Despite all of the things I've tried from various Google search results and the official KDE PPA, I can't seem to install Amarok 2.4 in 10.04. I always get 2.3.2.

From what I've been reading, 2.4 should be installable on 10.04, but I can't get it done. 

Anybody have any suggestions regarding this?

---

### Post by Dutch70 on 2011-04-02
Have you tried going to the following link to download it?
[[COLOR="RoyalBlue"]http://linux.softpedia.com/get/Multimedia/Audio/amaroK-2140.shtml[/COLOR]]("http://linux.softpedia.com/get/Multimedia/Audio/amaroK-2140.shtml")

---

### Post by shinkaide on 2011-04-02
That only redirects you to the official Amarok download page, which was the first thing I tried. :|

---

### Post by shinkaide on 2011-04-03
Never mind. I finally found a way to install Amarok 2.4 in Ubuntu 10.04.

I just followed the instructions found at the Amarok website:

```
sudo add-apt-repository ppa:kubuntu-ppa/backports
sudo apt-get update
```

Only difference being the last line (if Amarok has already been installed prior to this moment, methinks):

```
sudo apt-get -f dist-upgrade
```

That should install Amarok 2.4 without any problems and hopefully save some people the headache. =_=

---

