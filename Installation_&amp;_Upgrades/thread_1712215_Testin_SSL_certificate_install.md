---
title: "Testin SSL certificate install"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-22
I just installed a SSL  certificate I purchased from a CA.    I updated the virtual host server with the following.


[COLOR=Navy]SSLEngine on
SSLOptions +StrictRequire
[/COLOR][COLOR=Navy]SSLCertificateFile /home/website/ssl/certs/my_domain.crt 
SSLCertificateKeyFile /home/website/ssl/private/my_domain.key [/COLOR]

I am not sure if the certificate is installed and working . I am having problems getting my website software to recognize it.... It just does not work.

Does anyone know how I cat test to see if the SSL certificate is working?    Maybe i could create a simple *.php file or something.   

Any ideas?

---

### Post by spindler on 2011-03-22
I was able to test my ssl certificate using the following tool.

[http://www.digicert.com/help/](http://www.digicert.com/help/)

The output stated the following:

**No certificates were found.**

 **Output from 'openssl s_client' command:**




I am using the following instructions to edit the openssl.cnf file.

[https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr](https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr)

Why would I get this error?

---

