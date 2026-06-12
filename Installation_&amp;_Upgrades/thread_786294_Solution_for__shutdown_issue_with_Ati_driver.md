---
title: "Solution for  shutdown issue with Ati driver"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by miciurin on 2008-05-08
I have seen a number of posts where people report a shutdown / reboot system block after the Ati restricted driver is enbled. The user Lesergi has posted a solution and it seems that it is working. Here it is:

You must edit the file /etc/ati/authatieventsd.sh.

The suggestion is to update the change by changing

XDM_AUTH_MASK=/var/lib/xdm/authdir/authfiles/A$1*

to:

XDM_AUTH_MASK=/var/run/xauth/A$1*

---

### Post by cookier on 2008-05-08
And how can we edit that? 
Sry but i m new to ubuntu...

---

