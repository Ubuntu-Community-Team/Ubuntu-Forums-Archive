---
title: "upgrading to 8.04 from server 7.04"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by schneiderman on 2008-06-01
Hi all,
I am currently running a home server on 7.04 command line and I would like to upgrade to a graphical 8.04 hardy. I was just wondering if someone could explain the simplest way of doing this.

thank you,
Schneiderman

---

### Post by Pumalite on 2008-06-01
7.04>7.10>8.04
Make sure your system is well updated and remove all third parties from your /etc/apt/sources.list
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by schneiderman on 2008-06-01
> **Pumalite said:**
> 7.04>7.10>8.04
Make sure your system is well updated and remove all third parties from your /etc/apt/sources.list
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
that seems to upgrade to server 8.04. I wanted to upgrade to the graphical version of 8.04

---

### Post by zvacet on 2008-06-01
Follow **Pumalite´s** advice and upgrade to Hardy server.Be sure that you have this lines in your source list

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

Then you can install desktop of your choice 

1.GNOME

```
sudo aptitude install ubuntu-desktop
```

2.KDE

```
sudo aptitude install kubuntu-desktop
```

3.XFCE

```
sudo aptitude install xubuntu-desktop
```

---

