---
title: "saving repositories"
date: 2016-07-01
forum: Installation &amp; Upgrades
---

### Post by uwe-bungto on 2016-07-01
I am going to upgrade from 14.04LTS to 16.04 LTS, actually a clean install.
Is there a way to save the repositories I have been using?
thanks

---

### Post by grahammechanical on 2016-07-01
Why would you want to do that? Each version of Ubuntu has its own set of repositories on the Ubuntu servers. Mixing the repositories from more than one version of Ubuntu will cause all kinds of package conflicts.

Anyway, the list of repositories, called software sources, are just text files. They can be copied like any other text file. They are at /etc/apt/

Regards

---

### Post by uwe-bungto on 2016-07-02
I thought there is a simpler way that typing in sudo add-apt-repository ppa:user/ppa-name a half dozen times on each box.
I also noticed that sudo add-apt-repository ppa:user/ppa-name without the distro name (trusty or vivid etc) will actually find the distro you have installed or return distro not found. I seems that a number of PPA's have stopped the last few updates.

---

### Post by howefield on 2016-07-02
Suppose you could do something like..

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*.list > ~/sources.list
```

which will make a new sources.list file saved to your home folder which contains all repositories listed within sources.list and sources.list.d

---

### Post by uwe-bungto on 2016-07-02
> **howefield said:**
> Suppose you could do something like..

```
cat /etc/apt/sources.list /etc/apt/sources.list.d/*.list > ~/sources.list
```

which will make a new sources.list file saved to your home folder which contains all repositories listed within sources.list and sources.list.d

Thanks

---

