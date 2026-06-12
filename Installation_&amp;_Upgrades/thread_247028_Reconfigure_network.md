---
title: "Reconfigure network?"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by SyBorg on 2006-08-30
Hi,

I have performed a test server installation on a machine, then I moved the hard disk to a new machine.
Everything was fine but the network, eth0 was not coming up.

How I solved was quite simple:

sudo grep eth /etc/*

Found that the previous eth card mac address was recorded in iftab, so

dmesg | grep eth

Found the new mac address and changed /etc/iftab accordingly, restarted network, everything fine now

I wonder if there is any way to bring up the original (through dpkg-reconfigure I guess?) installation dialogs to set up networking

---

