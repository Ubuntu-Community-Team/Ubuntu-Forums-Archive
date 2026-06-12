---
title: "Apache2 Not Starting on Boot"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by Holzmann on 2007-03-25
I followed the instructions [here]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/httpd.html") on how to install Apache2 as well as HTTPS configuration, including how to create Self-Signed Certificate.

Now of course, when ever I start the machine, Apache2 is not automatically started. I have to start it manually and enter a passphrase.

Anyone know how to configure it to this automatically on start-up?

---

### Post by Holzmann on 2007-04-01
Bump for replies?

---

### Post by sjpwong on 2007-04-03
Unfortunately, you have to remove the password from the key if you want the certificate to be able to be read automatically when Apache starts.

You can remove the password using openssl, look here:

[http://www.webpipe.net/howto/Create_ssl_certificate#1a-_Remove_the_password_from_the_key](http://www.webpipe.net/howto/Create_ssl_certificate#1a-_Remove_the_password_from_the_key)

Good luck!

---

