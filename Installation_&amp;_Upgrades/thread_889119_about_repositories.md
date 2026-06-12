---
title: "about repositories"
date: 2008-08-13
forum: Installation &amp; Upgrades
---

### Post by milenmk on 2008-08-13
Two days ago I've installed 8.04.Tiping lsb_release -a it shows me Description:	Ubuntu 8.04.1
Release:	8.04

I have two problems
What should I type in System>administration>third party software so I can get the last repositories.I want to do that(a friend of mine advice me to) because I can't update Deluge to the newest version

---

### Post by kostkon on 2008-08-13
You can use their PPA, you'll find it [here]("https://launchpad.net/~deluge-team/+archive"). You'll need to add the first line, for Hardy (i.e. Ubuntu 8.04) that would be
```
deb http://ppa.launchpad.net/deluge-team/ubuntu hardy main
```

---

### Post by milenmk on 2008-08-13
Thanks a lot.I also found a few others

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

I hope they could be useful

---

### Post by kostkon on 2008-08-13
> **milenmk said:**
> Thanks a lot.I also found a few others

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

I hope they could be useful
But these are the default Ubuntu repositories and you already have them!!!

---

