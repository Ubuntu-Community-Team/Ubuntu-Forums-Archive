---
title: "Enable ssl"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by karnprakash on 2008-09-01
i have ubuntu 8.04 server edition with LAMP server. i had already configure the apache with mod_jk configuration.

Now i want to enable the SSL(self issued certificate)into the apache. how to do that.

Plz help me:confused:

---

### Post by datajelly on 2008-09-05
karnprakash,

I have a tutorial that can guide you through installing a certificate that you got from purchasing an SSL cert. I'm hoping that setting up a self-signed certificate would be similar:

[http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html]("http://blog.datajelly.com/2007/12/using-apache-for-ssl-offloading-and.html")

The basic setup would be to add a section to your Apache configuration (virtual host) as follows:

```
<VirtualHost *:443>
ServerName www.domain.com:443
SSLEngine on
SSLCipherSuite ALL:!ADH:! EXPORT56:RC4+RSA:+HIGH:+MEDIUM:+LOW:+SSLv2:+EXP:+eNULL
SSLCertificateFile "/path/to/cert.pem"
SSLCertificateKeyFile "/path/to/private.pem"
BrowserMatch ".*MSIE.*" nokeepalive ssl-unclean-shutdown downgrade-1.0 force-response-1.0
<Location />
ProxyPass http://appserver:8080/
ProxyPassReverse https://www.domain.com/
</Location>
</VirtualHost>
```

The trick is to save your self-signed certificate as /path/to/private.pem

---

