---
title: "Postfix wit SASL/TLS"
date: 2010-02-23
forum: Installation &amp; Upgrades
---

### Post by VaineDragon on 2010-02-23
Setting up my mail server for secure e-mail, using this web article to do so.
[https://help.ubuntu.com/community/Postfix](https://help.ubuntu.com/community/Postfix)

I don't find this smtpd.conf in /etc/postfix folder, do I need to create this file?

Next edit /etc/postfix/sasl/smtpd.conf and add the following lines: pwcheck_method: saslauthd
mech_list: plain login

---

