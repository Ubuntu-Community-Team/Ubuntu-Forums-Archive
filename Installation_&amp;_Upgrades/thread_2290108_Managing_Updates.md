---
title: "Managing Updates"
date: 2015-08-09
forum: Installation &amp; Upgrades
---

### Post by cranerja on 2015-08-09
I have a computer that I use as a file server for about ten other computers in my network, all running Ubuntu 14.04. I have very poor internet access and would like the main machine to automatically download the updates and have all of the computers in my network 'download' the updates from the server. Is this possible, and if so, how?

---

### Post by matt_symes on 2015-08-09
Hi

Take a look at either

apt-cacher

Or 

apt-cacher-ng

I have never used either but they look similar to a tool that I have used called apt-mirror. (I have mirrored the entire repository and some  ppas for reasons I won't go into).

They may be just what you need. If so then you'll have to set up an Apache server.

Another option maybe

apt-zip

Kind regards

---

