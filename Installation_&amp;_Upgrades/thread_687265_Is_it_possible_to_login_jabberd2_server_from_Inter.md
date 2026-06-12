---
title: "Is it possible to login jabberd2 server from Internet?????"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by megerdin on 2008-02-04
Is it possible to login jabberd2 server from Internet?????


I m jabbberd fan and...
I m running jabberd2 server for my lan user.
I want to let my user login from Internet.

Thats why I tried, and can't login ..

when I tried I see following error in log.

> Feb  4 17:33:33 admin-3 jabberd/c2s[17574]: [8] [202.56.7.168, port=1158] connect
Feb  4 17:33:34 admin-3 jabberd/c2s[17574]: [8] [202.56.7.168, port=1158] error: XML parse error (not well-formed (invalid token))
Feb  4 17:33:34 admin-3 jabberd/c2s[17574]: [8] [202.56.7.168, port=1158] disconnect


But for my LAN user it just working fine.


> Feb  4 17:32:57 admin-3 jabberd/c2s[17574]: [7] [192.168.0.113, port=37216] connect
Feb  4 17:32:57 admin-3 jabberd/c2s[17574]: [7] SASL authentication succeeded: mechanism=DIGEST-MD5; authzid=sumon@192.168.20.150
Feb  4 17:32:57 admin-3 jabberd/c2s[17574]: [7] bound: jid=sumon@192.168.20.150/Home
Feb  4 17:32:57 admin-3 jabberd/c2s[17574]: [7] requesting session: jid=sumon@192.168.20.150/Home
Feb  4 17:32:57 admin-3 jabberd/sm[17557]: session started: jid=sumon@192.168.20.150/Home


If its  possible to login from Internet .. then how? please help me.

note: I m not using allow/deny ip  section in c2s file.


Thanks In adv.

---

### Post by megerdin on 2008-02-04
Problem solved!!


yes possible !
i just open 5222 port for my server in firewall.

And its just works fine

---

