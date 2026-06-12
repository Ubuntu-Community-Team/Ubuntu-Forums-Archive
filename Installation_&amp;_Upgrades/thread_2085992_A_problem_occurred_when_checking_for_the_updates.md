---
title: "A problem occurred when checking for the updates"
date: 2012-11-19
forum: Installation &amp; Upgrades
---

### Post by mamboknave on 2012-11-19
[I am still with 10.04 64b and I must stick to it until mid next year]

Today, ALL OF A SUDDEN, a red/warning sign appeared on the panel.

It indicates that "A problem occurred when checking for the updates"

The Update Manager says that "Your system is up-to-date" but I notice it stops checking after 50 downloads while until yesterday it was going beyond 70.

Then I've done:

$ sudo apt-get update
Get:1 [http://linux.dropbox.com](http://linux.dropbox.com) lucid Release.gpg [489B]
... (48 lines removed for clarity)
Hit [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources
Fetched 4,117B in 1s (3,854B/s)
Reading package lists... Done

$ sudo apt-get upgrade -f
Reading package lists... Done  
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Also, 'sudo apt-get clean' does not resolve anything.

Can someone PLEASE help me here?

Thanks a lot...

---

### Post by mamboknave on 2012-11-19
RESOLVED:

It happened that yesterday I did (intentionally & for specific purposes) link /usr/bin/python to /usr/bin/python3.1 while it must remain linked to /usr/bin/python2.6

The issue was resolved by restoring the original link.

---

