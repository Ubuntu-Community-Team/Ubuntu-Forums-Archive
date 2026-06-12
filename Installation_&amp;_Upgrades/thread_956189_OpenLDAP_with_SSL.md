---
title: "OpenLDAP with SSL"
date: 2008-10-23
forum: Installation &amp; Upgrades
---

### Post by tuananh1973 on 2008-10-23
Hello,

I tried to configure openldap server with ssl on Ubuntu 8.04. I created a server certificate (self-sign), configured slapd.conf as follow.

TLSCACertificateFile server.pem
TLSCertificateFile server.pem
TLSCertificateKeyFile server.pem 

I restarted slapd then tried 

openssl s_client -connect localhost:636 -showcerts 

it told me that 

connect: Connection refused
connect:errno=29

I also tried with Centos, it just works just fine.

Please help,
Tuan Anh

---

### Post by flyonthewall on 2009-04-27
Basically this means your slapd server isn't running on the port you specified. Does it give any output when you try to start the service? 
(You start it by running /etc/init.d/slapd start)

Personally my slapd won't start.
I get the following error message:

```
main: TLS init def ctx failed: -64
```

---

