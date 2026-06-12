---
title: "Apt broken (libxt6) -- Can't Install/Update anything"
date: 2005-04-23
forum: Installation &amp; Upgrades
---

### Post by darkJester on 2005-04-23
Hello. I've been running Warty for a while. I tried going through some install procedures for getting Java onboard so I could use FreeMind. When I tried to do so, I got the following error:

> Preparing to replace libxt6 4.3.0.dfsg.1-6ubuntu25.1 (using .../libxt6_6.8.2-10_i386.deb) ...
Unpacking replacement libxt6 ...
dpkg: error processing /var/cache/apt/archives/libxt6_6.8.2-10_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/lib/X11/app-defaults', which is also in package xnview
Errors were encountered while processing:
 /var/cache/apt/archives/libxt6_6.8.2-10_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

This happens when I run "apt-get -f install", "apt-get upgrade", "apt-get update"... pretty much any "apt-get" command, including "apt-get remove xnview".

This is really frustrating  ](*,) , so any help would be greatly appreciated!  :grin:

---

