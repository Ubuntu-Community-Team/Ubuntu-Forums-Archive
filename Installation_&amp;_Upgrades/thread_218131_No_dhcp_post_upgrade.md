---
title: "No dhcp post upgrade"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by brumblebee on 2006-07-18
Hi Folks

We've got a network with 10 clients running off it and so I've tried upgrading one client as a test.  But, after the upgrade I was unable to log in using a network ID.  I have created a new local user and logging in I see that I am not picking up dhcp.  

I have tried to amend the etc/network/interfaces file but the login that I have created does not appear to have admin rights.  Mind you the following 2 lines are in the file

auto eth0
iface eth0 inet dhcp

which I've read is sufficient for the client to get dhcp.  Any suggestions gratefully accepted.

---

### Post by LordRaiden on 2006-07-18
sudo dhclient was what I used.

---

