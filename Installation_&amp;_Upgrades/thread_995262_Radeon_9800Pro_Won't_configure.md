---
title: "Radeon 9800Pro Won't configure"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by Bluefox79 on 2008-11-27
I managed to get as far as installing ati's drivers and catalyst, the install walkthrough then said log in through su and run /usr/X11R6/bin/aticonfig --initial to finish setup and restart.
heres the output.
<--
omega@OmegaMachine:~$ su
Password: 
root@OmegaMachine:/home/omega# /usr/X11R6/bin/aticonfig --initial
Uninitialised file found, configuring.
Segmentation fault
root@OmegaMachine:/home/omega# 
-->

So in further exploring I find out that a segfault is an error directly resulting in a denial of access to files to be read or written or whatever, look I'm an ubuntu Noob and got this far, can someone please explain why it won't configure or tell me what I'm doing wrong?

---

