---
title: "Upgrade Ubuntu using socks connection"
date: 2011-11-25
forum: Installation &amp; Upgrades
---

### Post by anch0 on 2011-11-25
I'm trying to upgrade from natty to oneiric using do-release-upgrade. The problem is that I have internet only through socks using a local shh tunnel connection created by using: ssh -g -D 8888 user@ip. The tunnel works great with firefox and using tsocks or proxychains with other applications, also works with do-release-upgrade at first stage, but after the "downloading upgrade tool" it clears the screen and seems like a call to apt-get or synaptic (or is it aptitude?) and all the connections tries keeps failing.
I've tried replacing apt-get in /usr/bin with a script that invokes first proxychains with parameters apt-get and $@, but that doesn't work either.
Please help to upgrade and many thanks.

---

