---
title: "Upgrade to 18.04 with a new hard disk"
date: 2019-01-31
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2019-01-31
Rant: all my upgrades from Ubuntu 6.04 failed, I don't extpect different this time either ;-)
Different this time is that I upgrade (fresh installation) to a new hard disk (460 GB SSD) and keep my old hard disk (240 GB SSD).

This machine is running behind a router (NAT) following tasks:
nginx, letsencrypt, php, docker & docker-compose, ... which I believe is just to install and use old config files to get it running again.

mysql is a challenge. I use currently Ubuntu 16.04. How do I get the data to the new hard disk, as mariadb and running? (best / fast)
how do I move workbench over?

Thunderbird, firefox, chrome, ... I find on the internet receipts how to setup with my old collected data. 
Should I use a different email program? I use gmail and maybe another client would be better?

My plan is to plug in the 480 GB onto the spot of the 240 GB and 240 GB onto another SCSI port. Then install Ubuntu 18.04, use the old info of /etc/fstab to mount my data directory, and add the old 240 GB as a /home directory

As more I think about it as more confused I get how to do.

Can you give me some hints, suggestions, warnings, .... please.

---

