---
title: "installing secureswan ikev2 vpn server"
date: 2017-07-29
forum: Installation &amp; Upgrades
---

### Post by dmwilliams2 on 2017-07-29
Im trying to install an ikev2 vpn server.
i can't even get it to bind to port 500
500 is the default port right?

this is my ipsec.conf
i think something is wrong with this configuration file

what is rightsourceip?

```
conn ikev2-vpn    auto=add
    compress=no
    type=tunnel
    keyexchange=ikev2
    fragmentation=yes
    forceencaps=yes
    ike=aes256-sha1-modp1024,3des-sha1-modp1024!
    esp=aes256-sha1,3des-sha1!
    dpdaction=clear
    dpddelay=300s
    rekey=no
    left=%any
    leftid=173.255.211.244
    leftcert=/etc/ipsec.d/certs/vpn-server-cert.pem
    leftsendcert=always
    leftsubnet=0.0.0.0/0
    right=%any
    rightid=%any
    rightauth=eap-mschapv2
    rightdns=8.8.8.8,8.8.4.4
    rightsourceip=173.255.211.244
    rightsendcert=never
    eap_identity=%identity
```

---

### Post by dmwilliams2 on 2017-07-29
typing random stuff into the ipsec.conf
only give me an error on 

service strongswan restart

and my configuration file had no errors the whole time.

port 500 and 4500 remain closed.

---

### Post by dmwilliams2 on 2017-07-29
i really think its not even binding to the port.
telnet doesn't work even when i ssh tunnel.

---

### Post by dmwilliams2 on 2017-07-29
[COLOR=#000000]rightsourceip is probably a local ip?
10.0.1.5[/COLOR]

---

