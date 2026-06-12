---
title: "Pidgin not working behind proxy for MSN"
date: 2008-04-13
forum: Installation &amp; Upgrades
---

### Post by acidsolution on 2008-04-13
Problem connecting MSN from PIDGIN in Gutsy Gibbon..
yahoo and gtalk are working fine 
I am behind the college proxy but msn in windows works well fine 
this is what i get everytime 
any help???
> 
Unable to authenticate: Unable to connect

Pidgin will not attempt to reconnect the account until you correct the error and re-enable the account.

---

### Post by twist2b on 2008-04-13
I opened my pidgen, so type in the proper places and see if it works. Deleted your msn account and start over (inside pidgeon)
Server: messenger.hotmail.com
Port: 1863

You might have to use http method 0_o

---

### Post by acidsolution on 2008-04-13
i already tried all u told 
but still cant get out of this problem

---

### Post by akadruid on 2008-07-07
For anyone still trying to solve this issue, try deleting all passport.com and live.com certificates from ~/.purple/certificates/x509/tls_peers.  Worked for me.

---

