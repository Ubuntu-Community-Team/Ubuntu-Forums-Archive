---
title: "Postfix password and TLS authentication issue"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by rc5501 on 2008-03-22
This is my first installation of ubuntu server.  I am running 7.10 and have ispconfig installed.

I am running postfix with Courier POP3 and IMAP.  I created TLS certificates according to the "Perfect Ubuntu Server" tutorial which is all over google.  My problem is that my server does not seem to be accepting my password.  It says that a conncetion is established but that the password was rejected.

I can create a successful internal Telnet Connection and according to the Telent output my TLS settings should be correct, however my mail client said that the server did not accept TLS connections. Any help would be appreciated.  My server runs good outside of this issue.

Also I have a MX record.  mail.mydomain.com and have a A record pointed to my external ip with port forwarding to my server.

I am running smtp port 587 due to my isp blocking 25, As i said i sucessfully created a Telnet connection using that port. and changed the default port within the postfix master configuration file.

Thanks a lot for any help you guys can give

---

