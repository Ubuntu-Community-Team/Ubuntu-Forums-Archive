---
title: "Which repo provides Opera"
date: 2007-08-15
forum: Installation &amp; Upgrades
---

### Post by satimis on 2007-08-15
Hi folks,


Ubuntu 7.04 lamp server


I need to install Opera

$ apt-cache policy opera```

opera:
  Installed: (none)
  Candidate: (none)
  Version table:

```

$ sudo apt-get install opera
Password:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

```
Not found.


$ grep -v '^#' /etc/apt/sources.list | grep -v '^$' | sort```

deb http://archive.canonical.com/ubuntu feisty-commercial main
deb http://hk.archive.ubuntu.com/ubuntu/ feisty main restricted
deb http://hk.archive.ubuntu.com/ubuntu/ feisty multiverse
deb http://hk.archive.ubuntu.com/ubuntu/ feisty universe
deb http://hk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://hk.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe

```

Please advise which repo I have to add to get Opera and how to add it?  TIA


B.R.
satimis

---

### Post by kostkon on 2007-08-15
Strange, because it is provided by the commercial repository and I see that you have this repository in your sources.list.

Please, do a
```
sudo apt-get update
```

and retry.

---

### Post by satimis on 2007-08-15
> **kostkon said:**
> Strange, because it is provided by the commercial repository and I see that you have this repository in your sources.list.

Please, do a
```
sudo apt-get update
```

and retry.
Hi kostkon,

I ran it already and also upgrade some packages.  Then re-ran;

$ sudo apt-get install Opera

Still the same.


B.R.
satimis

---

### Post by kostkon on 2007-08-15
The package is called *opera*, so you should do
```
sudo apt-get install opera
```

---

### Post by nickb834 on 2007-08-15
yup, that definately works - just done it myself, don't forget CaSe SeNsItIvE ;-)

---

### Post by satimis on 2007-08-15
> **nickb834 said:**
> yup, that definately works - just done it myself, don't forget CaSe SeNsItIvE ;-)
Hi nickb834 and kostkon


Re-tried

$ sudo apt-get update
No complaint

$ sudo apt-get install opera```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package opera is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package opera has no installation candidate

```
Not found.

B.R.
satimis

---

### Post by jim_p on 2007-08-15
I have this as my opera repo

```
deb http://deb.opera.com/opera etch non-free
```

I can verify it works since it updated Opera from 9.0 to 9.1 to 9.2 to 9.22
but it cant update to the recent 9.23 release.


I also found that this repo contains Opera

```
deb http://archive.canonical.com/ubuntu feisty-commercial main

```

---

### Post by zvacet on 2007-08-15
Why don´t you just download it from this page

[http://www.opera.com/download/]("http://www.opera.com/download/")

---

### Post by satimis on 2007-08-15
Hi folks,


Tks for your advice.


Now I know why I can't install Opera on repo.  This is a 64 bit box, a server.  Opera is a 32bit package.  I have Firefox running on this box.  The only reason for installing Opera is its addon function on magnifying image text.  I may turn back to install image zoom on Firefox.

Is this addon package available on repo?  Please advise how to install it.  TIA


B.R.
satimis

---

### Post by catnappist on 2007-08-15
I just got it with the add/remove thing, but it wasn't there when I looked and I still haven't figured out how to work the .deb thing.  Fortunately, I was able to install it thru the synaptic package manager.  Just thought I'd... throw that out there.

---

### Post by catnappist on 2007-08-15
Hmmmm.  Just fired up opera and the writing is really...really tiny.  I raised the font and it's still so tiny I can barely see what I'm doing. Is this normal?

---

### Post by satimis on 2007-08-15
> **catnappist said:**
> Hmmmm.  Just fired up opera and the writing is really...really tiny.  I raised the font and it's still so tiny I can barely see what I'm doing. Is this normal?
Hi catnappist,

I tried both Opera and Kmeg (K Magnifier) on another PC, Ubuntu 7.04 desktop.  Both worked magnifying the text on images.  But the magnified fonts were not very clear, depending on their size.  However they serve my need.


Edit:
On Opera;
to magnify text on images - [Ctrl]+[mousewheel)


satimis

---

### Post by catnappist on 2007-08-16
I have 7.04 too. Raising the fonts didn't have any effect at all. Since we're talking about fonts that couldn't have been half the size of the smallest letters on this page, guess I'll stick with Mozilla. I just wanted to try it out anyway. Thanks.

---

### Post by catnappist on 2007-08-16
OH! Ctrl-mousewheel, I didn't get that till now (not known for my quickness). Thanks!

---

