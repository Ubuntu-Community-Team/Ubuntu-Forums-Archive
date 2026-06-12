---
title: "Can't get dovecot configured"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by grizdog on 2012-09-23
Hello,

I recently upgraded to 12.04, and haven't been able to get dovecot working.  I'm posting here because the dovecot package I got differs from what it talks about on the dovecot wiki, notable the nonexistence of the doc directory.

The problem appears to be one of authentication.  Here is a sample from the logfile:

```
dovecot: imap-login: Disconnected (no auth attempts): rip=132.178.151.219, lip=24.117.84.87, TLS handshaking: SSL_accept() failed: error:14094412:SSL routines:SSL3_READ_BYTES:sslv3 alert bad certificate: SSL alert number 42

```I tried using the certificate from my old installation, and then downloaded the mkcert.sh script from the dovecot site and rebuilt the cert (I also downloaded the config file for the script and edited it).  I've built certs before, I hope I got that right.

When I start thunderbird, I also get one of those ephemeral messages that says it could not connect to my mail server - and I don't start thunderbird until I have issued a restart command for dovecot.

I'm wondering if this is related to PAM?  I really don't know anything about PAM, so I tried to follow all the directions, but I remain nervous about it.

Thanks for any help.

Alex

---

### Post by grizdog on 2012-09-23
After looking further into this, I'm thinking maybe the problem is with postfix, even though all the entries in the mail log seem to be about dovecot.

All the documentation I can find about these two seems to be a just a little out of date - the config files have slightly different names or locations.  Is there a clear guide anywhere?  All I want to do is set up my desktop machine as a mail server - nothing fancy, except I would like SSL and TSL, but I can live without that at first if I can just get the thing going, and then add the security once I have a working configuration.

Thanks for any help.

Alex

---

### Post by grizdog on 2012-09-25
OK, even though all the error messages were about dovecot, tweaking the configuration or postfix did the trick.  Thanks to anyone who spent any time thinking about this.

I changed several things in the postfix configuration, so I'm not sure what it was, but I have a very vanilla implementation of both tools, and it works fine.

---

