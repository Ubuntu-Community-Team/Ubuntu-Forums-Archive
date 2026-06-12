---
title: "no imap in 6.06?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Locke2053 on 2006-06-04
I've had a 5.04 dovecot server doing my IMAP for a long time. I just installed a fresh copy of 6.06, and did an apt-get install dovecot-imap. But there was no imap service. And when I try to start int manually, it also fails:

root@machine:~# /etc/init.d/dovecot start
sed: can't read /etc/inetd.conf: No such file or directory

What's going on? I want my email.

---

