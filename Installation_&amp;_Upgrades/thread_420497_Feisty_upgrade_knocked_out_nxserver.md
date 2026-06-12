---
title: "Feisty upgrade knocked out nxserver"
date: 2007-04-23
forum: Installation &amp; Upgrades
---

### Post by malandro95 on 2007-04-23
I had Edgy running on my box at home and I decided to update it via a freenx session using the normal method (clicking the button on the upgrade window).

Everything looked great when the update finished, and I decided to reboot the machine, just to make sure that all settings took effect.  Once the box was rebooted, I could no longer connect via freenx.  I am still connecting via SSH.

I have tried many things, including adding nxserver users, redoing the nxsetup both with private and the nomachine key.  No matter what I do, I get some type of permission denied error.  My current error is this:


> NX> 203 NXSSH running with pid: 7212
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 200 Connected to address: 192.168.0.10 on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 1.4.0-45-SVN OS (GPL)
NX> 105 /usr/lib/nx/nxserver: line 458: /dev/null: Permission denied


Has anyone successfully upgraded edgy to feisty without breaking freenx?  

Also, I have changed so many things that I may have made things worse.  Any ideas?  Thanks!

---

