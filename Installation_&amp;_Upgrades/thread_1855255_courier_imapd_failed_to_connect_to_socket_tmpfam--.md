---
title: "courier imapd failed to connect to socket /tmp/fam--"
date: 2011-10-05
forum: Installation &amp; Upgrades
---

### Post by randymized on 2011-10-05
I am trying to set up an email server on Natty using postfix and using courier to handle imap connections.  Mail appears to be received ok, but if I try to send mail using imap, mail.log includes numerous entries like > <time> <server-name> imapd: Failed to connect to socket /tmp/fam--From what I am able to determine, the /tmp/fam-- socket the message refers to is part of the interface to Gamin, although I am unable to find definitive documentation confirming that.  /etc/gamin/gaminrc does not appear to provide any means to set or change the socket location.  I can also find no means to set or change this location in courier configuration files.

> ps -A|grep gam shows that gam_server is running, but the socket is not present in /tmp.  Interestingly, I find that gam_server is running on another server that includes a functional email system (which I am trying to duplicate), but /tmp/fam-- is not present on that server either.

I don't know what else I can do to either diagnose or fix the problem and would appreciate any suggestions that might lead toward resolution.

---

