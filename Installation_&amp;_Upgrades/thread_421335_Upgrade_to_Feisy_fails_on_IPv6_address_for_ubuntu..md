---
title: "Upgrade to Feisy fails on IPv6 address for ubuntu.com?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by kylog on 2007-04-24
I'm running kubuntu 6.10 for i686.  The application manager asks me if I want to do a Dist Upgrade, I agree, and it downloads files for a while, apprently with some success, but then stalls for a long time, eventually giving me a dialog "error during update" with a number of lines of the form:

Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg) Cannot initiate the connection to us.archive.ubuntu.com:80 (2001:6b0:e:2018::159). - connect (101 Network is unreachable) [IP: 2001:6b0:e:2018::159 80]

I've never done anything with IPv6 on this box, so I'm surprised to see those IPv6 addresses.  I *can* ping us.archive.ubuntu.com, but of course I get an IPv4 address for it.

Thoughts?

Kylo

---

