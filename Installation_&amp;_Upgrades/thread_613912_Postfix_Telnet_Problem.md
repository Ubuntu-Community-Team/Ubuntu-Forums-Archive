---
title: "Postfix Telnet Problem"
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by bizman on 2007-11-15
When I have "smtpd_sasl_auth_enable = yes" in the main.cf file I only get the following when testing telnet with the localhost:

Connected to localhost.
Escape character is '^]'.
(At this point the terminal session is hung up and does nothing.)

However, when I comment "smtpd_sasl_auth_enable = yes" out of the main.cf, I get:

Connected to localhost.
Escape character is '^]'.
220 BizcenWebServer.bizcen.com ESMTP Postfix (Ubuntu)
(It all works as suggested in the install doc)

Any ideas would be appreciated.  I am new to Postfix and am struggling through the installation.

Thanks
John

---

