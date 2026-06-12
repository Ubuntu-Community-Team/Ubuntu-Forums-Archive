---
title: "sendmail problem"
date: 2006-02-22
forum: Installation &amp; Upgrades
---

### Post by joao_candido on 2006-02-22
Hi everyone.

Something's wrong with my sendmail server. I'm able to send e-mails but not to receive.

When i try to test in [http://www.dnsstuff.com](http://www.dnsstuff.com), i receive an error message that says conection refused by remote mailserver.

Wath's wrong?
Can anyone help me?

Thanks.

---

### Post by suRoot on 2006-02-22
First question is whether dnsstuff resolves your MX properly?  

Second question, did you tell sendmail to listen on the right interfaces?  You should have this in your sendmail.mc file:

```
dnl # DAEMON_OPTIONS(`Port=smtp,Addr=127.0.0.1, Name=MTA')
```

Third question, runnning a firewall?  Can you connect to port 25 from other machines on your LAN?

---

