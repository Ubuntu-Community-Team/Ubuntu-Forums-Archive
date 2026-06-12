---
title: "Installing programs from source without screwing up APT?"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by EtherBunny on 2007-05-31
Is there a way to install programs from source so that they can be easily removed or replaced later?

Suppose I want the very latest version of a package in the ubuntu repos. If I install it from source, then want to get back on the old version later, is there a way to install it so that It will be removed when I do an "apt-get install packageX"?

Basically, when I do a "make install", it seems to send everything flying off into my system and I really don't know how to get it back. It would be nice to just "apt-get remove packageX". 

Is this possible?

---

### Post by greybirds on 2007-05-31
Check out checkinstall in the universe repository. It creates a .deb file of the program you just compiled and installs the deb, which means it can be managed with Ubuntu's apt/synaptic/aptitude programs. 

Here's its web site: [http://asic-linux.com.mx/~izto/checkinstall/](http://asic-linux.com.mx/~izto/checkinstall/)

(Edited because I can't stop typing "it's" today for some reason.)

---

### Post by EtherBunny on 2007-05-31
Thanks!  That's just what I was looking for.

---

