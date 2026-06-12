---
title: "Trouble on Create Certificate in Freeradius"
date: 2007-10-04
forum: Installation &amp; Upgrades
---

### Post by realnormalman on 2007-10-04
Hi,
    
     Hey, any 1 know what is the error on this?


root@radius-desktop:/usr/local/openssl/ssl/misc# openssl ca -policy policy_anything -out newcert.pem -passin pass:whatever -key whatever -extensions xpserver_ext -extfile xpextensions -infiles newreq.pem
Using configuration from /usr/lib/ssl/openssl.cnf
unable to load CA private key
13049:error:0906D06C:PEM routines:PEM_read_bio:no start line:pem_lib.c:644:Expecting: ANY PRIVATE KEY


:confused::confused:

---

