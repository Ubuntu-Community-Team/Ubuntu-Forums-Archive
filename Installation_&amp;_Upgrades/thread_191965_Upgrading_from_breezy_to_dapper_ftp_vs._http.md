---
title: "Upgrading from breezy to dapper: ftp vs. http"
date: 2006-06-08
forum: Installation &amp; Upgrades
---

### Post by vinfred on 2006-06-08
I'm working behind a firewall that lets me use http but not ftp

I was running breezy up-to date
I started the update to Dapper thru Update manager

Everything went right until the installation procedure tried to download f-prot from [ftp://ftp.f-prot.com](ftp://ftp.f-prot.com)

I had to kill the process doing the ftp.
As a result the upgrade failed at the end (I hope) of the installation procedure

I've no idea on whether the post upgrade cleanup was done or not :confused: 

Each time I was using synaptic (to check for updates, or to download new packages) , it wanted to install f-prot.

I had to download the files fp-linux-ws.tar.gz and fp-linux-ws.tar.gz.md5 on another system then get the files locally to finally get synaptic usable.

I can assure that ftp.f-prot.com is NOT specified anywhere in my /etc/apt/sources.lis

The system seems to be usable. Except that I had to specify my proxy into /etc/environment

http_proxy="http://user:Pass@proxy:8080/

I tried to modify synaptic settings (network tab) but as soon as I apply the settings, synaptic hangs for ever using 100% CPU ](*,)

---

### Post by vinfred on 2006-06-12
Any Idea on whether the post install cleanup has been done ?
What can I check to be sure ?

---

