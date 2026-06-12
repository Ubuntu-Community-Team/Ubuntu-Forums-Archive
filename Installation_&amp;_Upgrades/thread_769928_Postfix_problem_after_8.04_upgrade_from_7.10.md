---
title: "Postfix problem after 8.04 upgrade from 7.10"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by arborrow on 2008-04-27
I was using postfix as my smtp (localhost) to send mail via thunderbird. Prior to the upgrade everything was working fine; however, after upgrading to 8.04 I cannot connect to the postfix server. Where should I look to see what changed and get things working again?

---

### Post by zazuge on 2008-04-30
you could scan your own ports with nmap -A 127.0.0.1 to see if smtp port is open or not maybethe postfix master is starting but not the smtpd module
take a lool at /etc/postfix/master.cf file
and check for your log 
grep postfix /var/log/syslog
tail -fn 60 /var/log/mail.log
tail -fn 60 /var/log/mail.err
and use this to inrement log level for tls
smtp_tls_loglevel = 2
hope that helps.

---

