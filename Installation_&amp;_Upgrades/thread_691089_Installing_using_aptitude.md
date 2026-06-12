---
title: "Installing using aptitude"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by vanderkerkoff on 2008-02-08
This may be a dumbass question but I'm not a proud man :-)

If I install lighttd say with aptitude, do I only have to remove the call to it in /etc/init.d in order to make it not try to start on startup?

I'm following these instructions to get php-cgi running with nginx and dont want all of lighttpd, only the spaen-fcgi stuff.

thanks in advance

---

### Post by vanderkerkoff on 2008-02-08
On a similar topic, I'm going to be using php to power my expression engine site, but I don't want apache to be installed.  

Well in fact I'm only going to be using the php-cgi to run it, I'm not sure how much php I need to be honest.

Anyway.

Is there an easy way to accomplish this with aptitude?  I tried installing it like

sudo aptitude install php5 

but it brings down a whole heap of apache2 shite that I don't need/want

Any help, greatly appreciated.

---

