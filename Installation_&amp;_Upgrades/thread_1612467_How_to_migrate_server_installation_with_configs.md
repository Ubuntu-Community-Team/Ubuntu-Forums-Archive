---
title: "How to migrate server installation with configs"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by bmk352 on 2010-11-03
I am looking to migrate my current Ubuntu 9.10 x86 server to a new machine and install Ubuntu 10.04 x64.  I am trying to find the best way to migrate all of my configs and ensure they work and haven't been able to find good enough information as of yet.
Right now I have installed 10.04 and ran the following commands to install all of the packages found on my current server to install on the new server:
dpkg --get-selections > installed-software
dpkg --set-selections < installed-software
dselect
This worked great to install all of the packages but now I am stuck at trying to figure out the best way to bring all of the config files as well as the mySQL database over to the new server.  I had read that using rsync might be best but I tried a blank rsync from /etc/ to /etc/ and that didn't go so well... so my question is this, what is the best, most efficient way of ensuring all of the various config files are brought over to the new server?

---

