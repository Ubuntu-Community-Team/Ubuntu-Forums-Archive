---
title: "sources.list is missing lots of stuff"
date: 2018-08-02
forum: Installation &amp; Upgrades
---

### Post by swilson2 on 2018-08-02
OK, I downloaded the latest server iso: ubuntu-18.04.1-live-server-amd64.iso, installed a bare bones server and typed the following:

apt-get update
apt-get upgrade
apt-get install subversion

and I get 
"package subversion has no installation candidate"

What is going on here?  How do I install Subversion now!?

---

### Post by Bashing-om on 2018-08-02
swilson2; Hello;
```

apt show subversion

```
shows it is available in the universe repository.

Do you have the universe repo enabled in you software sources ?

[INDENT]sounds likely to me
[/INDENT]

---

### Post by deadflowr on 2018-08-02
^^++1
subversion was moved to the community (universe) repository for 18.04.
Double check that's enabled
Easy to set if not, just run
```
sudo add-apt-repository universe
sudo apt update
```

---

### Post by swilson2 on 2018-08-10
My question is, why is universe not included by default?  It used to be.

---

### Post by #&amp;thj^% on 2018-08-10
Out of 3 installs all of mine had it by default.
```
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ bionic universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic universe
deb http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ bionic-updates universe
```

---

### Post by PaulW2U on 2018-08-10
> **swilson2 said:**
> My question is, why is universe not included by default?  It used to be.
See bug report -  [Only "main" component enabled after install]("https://bugs.launchpad.net/subiquity/+bug/1783129").

I don't understand everything that being discussed there but the bug report summary does reflect what caused you to post here.

---

### Post by swilson2 on 2018-08-31
The correct answer is DON'T DOWNLOAD THE ***LIVE*** VERSION!!!

Download this file in the alternate downloads:

ubuntu-18.04.1-server-amd64.iso

---

### Post by QIII on 2018-08-31
The answer actually appears to be:  fix committed and will be released in a few hours.

---

