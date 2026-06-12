---
title: "Upstart does not start all init scripts"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by bjoh on 2010-09-01
Hi everyone,

I recently upgraded my headless remote server from 8.04 to 10.04 and ever since, upstart does not start all init scripts in /etc/rc2.d (2 being the default runlevel).

It seems all native upstart scripts are started (good thing sshd has an upstart script, otherwise I#d be locked out), but I have to start manually everything in rc2.d.

I could not find any errors in dmesg and frankly don't know where else to look - as syslog is one of the daemons I have to start manually, I don't have much hope that anything can be found.

Has anyone encountered this before and knows what to do?

Any help would be greatly appreciated!

---

