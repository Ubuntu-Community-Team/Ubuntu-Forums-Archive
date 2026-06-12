---
title: "blank screen after hoary install on Inspiron 2200"
date: 2005-07-08
forum: Installation &amp; Upgrades
---

### Post by baza41 on 2005-07-08
Hi, can anyone help with this. I'm trying to get Hoary working on a Dell Inspiron 2200. It all seems to go OK until it boots to desktop where the screen goes blank. 

Thanx

---

### Post by baza41 on 2005-07-10
Well, no one responed so I worked on it and fixed  it. Others might find it useful to know that if you change intel i810 to vesa in the xorg.conf file it works fine. I've also got the internal wireless working too.

Baza

---

### Post by sean_worker on 2005-07-23
did you have to do anything special to get the wireless up and running?

I just installed and had the same video problem as you ... I'm going to boot back up, switch to tty1 with ctrl-alt-f1, log in, make the changes to the /etc/X11/xorg.conf file, and restart with "shutdown -r now".

---

