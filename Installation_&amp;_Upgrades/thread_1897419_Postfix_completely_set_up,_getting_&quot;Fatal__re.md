---
title: "Postfix completely set up, getting &quot;Fatal : remove private/tlsmgr permission denied&quot;"
date: 2011-12-19
forum: Installation &amp; Upgrades
---

### Post by nonaimer on 2011-12-19
Hello,

I am trying to configure my postfix server for two weeks now...
I finally found a tutorial that works on Ubuntu.

[http://www.debiantutorials.com/installing-postfix-with-mysql-backend-and-sasl-for-smtp-authentication/](http://www.debiantutorials.com/installing-postfix-with-mysql-backend-and-sasl-for-smtp-authentication/)

I set up everything as said, I did it many times, but I keep getting "Fatal : remove private/tlsmgr permission denied" in /var/log/mail.err and mail.log

I checked /var/spool/postfix/private/tlsmgr, postfix can read and write. Unless I checked the wrong directory, I don;t know what is wrong. This is the final step of the server configuration I need. Please help me out here, I desperately need to make it work! :confused:

---

