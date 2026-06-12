---
title: "amanda client install on Karmic"
date: 2010-02-07
forum: Installation &amp; Upgrades
---

### Post by cocoa117 on 2010-02-07
I have looked many places for good tutorial on configuration of amanda client with Karmic, but none of them are good enough. 

I basically got following message no matter what I change in Client side. 

1. I am using 64-bit Ubuntu Karmic client with 2.5.2p1 amanda-client with xinetd.

2. The user is backup, group is backup. 

3. The config file is located at /etc/amandahosts, and /var/backups/.amandahosts and /var/lib/amanda/.amandahosts using soft link to the /etc/amandahosts file. 

4. /etc/amandahosts file have following line.
192.168.0.14 backup amdump
The 192.168.0.14 is server IP address.

error message:
amandad: time 0.351: security_seterror(handle=0x22cfb10, driver=0x7f8054372920 (BSDTCP) error=user backup from hermes-ubunut-test.local is not allowed to execute the service noop: Please add "amdump" to the line in /var/backups/.amandahosts on the client)
amandad: time 0.351: accept error: user backup from hermes-ubunut-test.local is not allowed to execute the service noop: Please add "amdump" to the line in /var/backups/.amandahosts on the client
amandad: time 0.351: sending NAK pkt:
<<<<<
ERROR user backup from hermes-ubunut-test.local is not allowed to execute the service noop: Please add "amdump" to the line in /var/backups/.amandahosts on the client
>>>>>

Any ideas?

---

### Post by cocoa117 on 2010-02-07
I solved by change the /etc/amandahosts file with following line
hermes-ubunut-test.local backup amdump

I have no idea why I have to use this machine name then IP address.

---

