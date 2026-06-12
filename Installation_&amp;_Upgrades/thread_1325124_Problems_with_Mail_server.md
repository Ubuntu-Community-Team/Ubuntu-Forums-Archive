---
title: "Problems with Mail server"
date: 2009-11-13
forum: Installation &amp; Upgrades
---

### Post by marulu on 2009-11-13
I have setup Ubuntu 9.04 to replace out existing Redhat 9 email server.
I have dovecot and postfix. y server box ip is 192.168.100.200
From my Windows PC when I telnet 192.168.100.200 110 or telnet 192.168.100.200 143
I can access the emails but am unable to do so via Outlook or OE.
I have added the debug option in /etc/dovecot.conf
and it now tells me:
pop3-login: Disconnected (no auth attempts)
rip=192.168.100.3, lip=192.168.100.200, TLS:Disconnected

Can someone help me please?

---

