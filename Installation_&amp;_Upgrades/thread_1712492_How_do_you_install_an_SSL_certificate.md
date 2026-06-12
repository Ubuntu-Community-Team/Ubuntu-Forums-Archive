---
title: "How do you install an SSL certificate"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by spindler on 2011-03-22
I am attempting to install an SSL certificate.

I am using the following documents.

[https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr](https://help.ubuntu.com/10.10/serverguide/C/certificates-and-security.html#generating-a-csr)

This document tells me how to create the certificate.   I did this with little problems.

[https://help.ubuntu.com/10.10/serverguide/C/httpd.html](https://help.ubuntu.com/10.10/serverguide/C/httpd.html)

These documents tell me how to install it on Apache2.

Basically I enable SSL.

**sudo a2enmod ssl**
**sudo a2ensite default-ssl**

I then modify the default-ssl for the following two lines of code

[COLOR=#000000][COLOR=#0000bb]SSLCertificateFile [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]etc/ssl/certs[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]my_domain[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]com[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]crt 
SSLCertificateKeyFile [/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]etc/ssl/private[/COLOR][COLOR=#007700]/[/COLOR][COLOR=#0000bb]my_domain[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]key [/COLOR][/COLOR]
Then I need to enable the file and restart apache2.

sudo a2ensite default-ssl
sudo /etc/init.d/apache2 restart

This appears to be all I need to do.  HOWEVER, my ssl is not installed.... or I cannot see it. 

I am using the following website to test the ssl certificate.

[http://www.digicert.com/help/](http://www.digicert.com/help/)

I ran this tool and got the following error.

**No certificates were found.**

 **Output from 'openssl s_client' command:**


So I am not sure what to do.   Why is the openssl s_client even involved.  I only used this to create the certificate.  

Does anyone know of a better document to tell me step by step how to install the certificate?

Thanks,

Spindler

---

