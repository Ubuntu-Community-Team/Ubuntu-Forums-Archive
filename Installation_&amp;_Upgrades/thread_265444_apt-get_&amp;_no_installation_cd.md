---
title: "apt-get &amp; no installation cd"
date: 2006-09-26
forum: Installation &amp; Upgrades
---

### Post by McHenry on 2006-09-26
I am installing Ubuntu server onto a headless & diskless server.
I am using a CD ROM for the installation that will be removed once complete.

I tried this then appempted to install the OpenSSH server using:
apt-get install openssh-server

All went well until it prompted me to insert the Ubuntu installation CD into the CD ROM drive. The problem is I don't want this machine to use the CD ROM as it will be removed on the basic install is complete.

How can I stop apt-get asking for the CD in future ?

Thanks

---

### Post by aysiu on 2006-09-26
> **McHenry said:**
> 
How can I stop apt-get asking for the CD in future ? ```
sudo nano -B /etc/apt/sources.list
``` Delete or comment out (put a # sign in front of) the line that refers to the CD-ROM. Then save (Control-X, Y, Enter) and ```
sudo aptitude update
```

---

### Post by McHenry on 2006-09-26
I'm guessing these are processed in the order in which they appear.

My ISP has a repository that is not counted towards download quota so I'd be better placing this at the top of the list.

---

