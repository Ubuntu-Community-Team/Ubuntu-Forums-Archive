---
title: "Problem with Synaptic (Ripositories)"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by BlackFoxTR on 2008-01-16
Hi. 
Today i installed ubuntu 7.10 (i were using 7.04, everything were ok) first i got problem with internet speed. Cause of it i had problem with installation. Now i have problem with synaptic. i can not download ani package from synaptic. 

"Could not download all repository indexes"

Plus when i use terminal : 

```
root@fox-desktop:/home/fox# sudo apt-get updateIgn cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-tr
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-tr
20% [Connecting to us.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubu
root@fox-desktop:/home/fox# 
```

I'm able to ping to sites. My connection is ok now.

---

### Post by Pumalite on 2008-01-16
Change server. If not, post your sources.list

---

### Post by BlackFoxTR on 2008-01-16
Here is my source list
```
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://tr.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://tr.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://tr.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://tr.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

deb http://packages.medibuntu.org/ gutsy free non-free
```

---

### Post by Pumalite on 2008-01-16
Your sources are sparse but OK. Have you checked your connection and changed to different servers?

---

### Post by BlackFoxTR on 2008-01-16
i changed servers few times.us, tr and gb which i tried. and my connection is ok now. i'm online with linux n posting to forum :)

---

### Post by nero_86 on 2008-01-16
Control that proxy server are disabled/configured properly (if you have one).

---

### Post by BlackFoxTR on 2008-01-16
All set to "direct connection". but not help

---

### Post by BlackFoxTR on 2008-01-16
Somebody pls help. all my day finished cause of this problem :(
```
root@fox-desktop:/home/fox# sudo aptitude update
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]
0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

0% [Connecting to tr.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubuntu.com (1.0.0.0)]

```

---

### Post by Pumalite on 2008-01-16
Are you in a home, a University, a large company, or at home? Do you have a home LAN, a winmodem or a router? How do you connect to the Internet? Are you behind a proxy?

---

### Post by BlackFoxTR on 2008-01-17
i'm at office. i have wireless Router , but i connecting with cable. I have direct ADSL connection. I not using proxy. Last time i closed ipv6 settings. Cause my internet were so slow. Maybe it affect?

---

### Post by BlackFoxTR on 2008-01-17
Thanks everybody :) i solved problem. just put ipv6 settings to blacklist. now it works! :)

---

### Post by Pumalite on 2008-01-17
Good for you!

---

