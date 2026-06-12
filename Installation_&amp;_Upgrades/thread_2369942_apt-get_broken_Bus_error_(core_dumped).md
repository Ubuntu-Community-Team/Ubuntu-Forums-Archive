---
title: "apt-get broken: Bus error (core dumped)"
date: 2017-08-28
forum: Installation &amp; Upgrades
---

### Post by lucid weaver on 2017-08-28
apt-get has broken for me. I tried to re-install it from a .deb, without any luck. The text below is what I see when running `apt-get update`. Before trying to install from .deb I saw the 'Bus error' message when running as normal user and sudo, instead of different errors. I'm hoping I can fix this without having to re-install Kubuntu, because the setup afterwards would be my whole day, but that's my next step if no one here knows what to do.


```
prompt:~$ apt-get update
W: chmod 0700 of directory /var/lib/apt/lists/partial failed - SetupAPTPartialDirectory (1: Operation not permitted)
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
prompt:~$ sudo !!
sudo apt-get update
Bus error (core dumped)
```


Thanks in advance.

---

### Post by oldos2er on 2017-08-28
Which version of Ubuntu are you running? And which specific .deb file did you try to reinstall from?

---

### Post by lucid weaver on 2017-08-28
I'm on Kubuntu 16.04 and [https://packages.ubuntu.com/xenial/amd64/apt/download](https://packages.ubuntu.com/xenial/amd64/apt/download) but also the 14.04 version before that (stupidly). I also attempted installing aptitude as well: [https://packages.ubuntu.com/xenial/amd64/aptitude/download](https://packages.ubuntu.com/xenial/amd64/aptitude/download)

---

