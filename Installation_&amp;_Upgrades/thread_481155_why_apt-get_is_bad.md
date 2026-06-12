---
title: "why apt-get is bad"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by sdd231163 on 2007-06-22
apt-get is probably the fastest and all round best package manager there is.

but

I have found that whenever one apt-get instance is closed without completing it's progress (anything from a KILL signal to closing a terminal because I chose the wrong option in running it), other apt-get instances cannot start up because they think one is already running, which isn't true. this means that I can't connect to the internet, because the script to do so looks things up in apt-get. Obviously I can't update packages and this virtually grinds my system to a halt.

I know there is a fix using dpkg that restores  apt-get to being able to run until next time I break it but I can't find it on the net.

---

### Post by OoooMatron on 2007-06-22
delete the lock file. it tells you where it is in the error message. simple.

---

