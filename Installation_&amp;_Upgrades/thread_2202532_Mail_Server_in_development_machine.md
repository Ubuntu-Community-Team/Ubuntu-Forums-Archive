---
title: "Mail Server in development machine"
date: 2014-01-29
forum: Installation &amp; Upgrades
---

### Post by elim-qiu on 2014-01-29
I'd like to install a testing email server on my ubuntu 13.10 laptop (When everything is fine, replace my win7 server, with ubuntu).

(1) Is it possible?
(2) What's free and recommended?
(3) Any instruction/tutorial on that?

Thanks a lot for your help!

---

### Post by SeijiSensei on 2014-01-30
[https://help.ubuntu.com/12.04/serverguide/email-services.html](https://help.ubuntu.com/12.04/serverguide/email-services.html)

Is your Windows server running Exchange?  That's a pretty substantial transition given how integrated Exchange is with Active Directory.  You'll need to look into things like LDAP authentication against the AD user database as well as simply setting up a mail server.  I hope you're not intending on doing this for a large user population without a lot of advance planning.

---

### Post by elim-qiu on 2014-02-03
I have Kerio 6.7.2 mail server (older than Kerio connect) on windows 7 Ultimate 64 bit en.
The mail server is mainly used for a forum registration. No heavy traffics.

I just want use Ubuntu Desktop instead of Ubuntu Server for my server. This way I can do some development job easily on site. With modern hardware, the overhead of using Desktop GUI is not a concern  anymore to me.

My question is that is there any OS difference that will prevent me from installing mail server to Ubuntu Desktop? It the mail server guide for Ubuntu server can be used with Ubuntu desktop?

---

