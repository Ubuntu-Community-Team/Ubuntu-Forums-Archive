---
title: "dovecot error"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by VaineDragon on 2010-02-24
I was following this tutorial and now get this error with dovecot?
[https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)


[http://pastebin.com/iXBj156c](http://pastebin.com/iXBj156c)

---

### Post by Barriehie on 2010-02-24
> **VaineDragon said:**
> I was following this tutorial and now get this error with dovecot?
[https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)


[http://pastebin.com/iXBj156c](http://pastebin.com/iXBj156c)

How about attaching dovecot.conf so we can see the offending line???

---

### Post by VaineDragon on 2010-02-24
I commented out the offending lines, and now it seems to work. Just having major issues getting SASL/TLS to work, tried following this Ubuntu Community Tutorial.

[https://help.ubuntu.com/community/PostfixDovecotSASL](https://help.ubuntu.com/community/PostfixDovecotSASL)




[ATTACH]148080[/ATTACH]

---

### Post by VaineDragon on 2010-02-24
This is also an issue when using the tutorial it says to edit /etc/postfix/sasl/smtpd.conf this file does not exist in /ect/postfix/sasl folder empty?

Here is what the tutorial says to do?

Next edit /etc/postfix/sasl/smtpd.conf and add the following lines: 
pwcheck_method: saslauthd
mech_list: plain login

---

