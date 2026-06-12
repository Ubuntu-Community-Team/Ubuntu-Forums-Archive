---
title: "Upgraded Saucy to Trusty, mtp not working for android"
date: 2014-04-24
forum: Installation &amp; Upgrades
---

### Post by Teres_Vir on 2014-04-24
I upgraded from 13.10 to 14.04, and i can't connect my android phone (samsung galaxy I8552) anymore. It was working fine with Saucy.

I have installed libmtp, gmtp and mtp-tools. fuse is already installed. I tried to install go-mtpfs, but looks like the package could not be found !!

I checked lsusb, and it doesn't output anything when i connected the device. Also, the device is also not giving any indication that a connection is extablished, except that it starts charging.

$ lsusb
Bus 001 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Syslog also doesn't have anything.

Any help would be appreciated. Thanks in advance.

---

### Post by carl4926 on 2014-04-25
It's all working fine here
Actually it works from the live session too.

---

### Post by Teres_Vir on 2014-04-25
I'm sure about it.. I don't want to sound rude, but its not working "here".  Any suggestions?

---

### Post by Teres_Vir on 2014-04-26
I apologize to Carl.. It was some issue with the cable. I tried a different one, and its working now. Actually, its better now in Trusty.. Carl, Thanks for responding fast.

---

