---
title: "can I install both ssmtp and postfix ?"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by tom93 on 2008-04-03
I'm trying to configure sasl authentication and I'd like to be able to test it from the command line. 

With smtp, you can telnet to port 25 to test things, but sasl is not that simple.

I've used sasl with mutt and ssmtp, so I thought I'd try installing ssmtp and then use mutt configured with ssmtp to test my sasl setup.

The problem I'm running into is that when I try to install ssmtp, aptitude wants to remove postfix which I have configured and working and want to keep.

---

