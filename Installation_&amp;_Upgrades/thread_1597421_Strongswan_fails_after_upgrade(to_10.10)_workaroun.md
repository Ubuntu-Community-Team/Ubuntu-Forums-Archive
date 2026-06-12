---
title: "Strongswan fails after upgrade(to 10.10) workaround"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by Alfafa on 2010-10-15
Hi

I have stumbled upon a german who write about a workaround for strongswan not working in 10.10

Basically he writes you should load the plugins for the charon daemon in a specific order. So your configuration should be like:

/etc/strongswan.conf:        ...
        charon {
                       ...
                        load =  curl ldap aes des sha1 sha2 md5 random x509 pubkey pkcs1 pgp  dnskey pem openssl fips-prf xcbc hmac agent gmp attr kernel-netlink  socket-default farp eap-identity eap-aka eap-md5 eap-gtc eap-mschapv2 nm  dhcp resolve
                       ...


Original found at: [http://mopoinfo.vpn.uni-freiburg.de/node/99](http://mopoinfo.vpn.uni-freiburg.de/node/99)

---

