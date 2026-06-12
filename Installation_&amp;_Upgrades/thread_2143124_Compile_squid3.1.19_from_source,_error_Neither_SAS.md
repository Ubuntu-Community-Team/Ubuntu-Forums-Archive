---
title: "Compile squid3.1.19 from source, error: Neither SASL nor SASL2 found"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by jimmah6786 on 2013-05-07
Hey all, 

I am trying to comiple squid3 from source to get SSL enabled. 

```
sudo apt-get install build-essentials fakeroot devscripts openssl
sudo apt-get build-dep squid3
sudo apt-get source squid3
```

When I do a 
```
debuild -us -uc -b 
```
I get
```
error: Neither SASL nor SASL2 found
```

I verified I have SASL2 installed, I even did a 
```
sudo apt-get install libsasl2-2
```

Heres the last lines of the buiid error
```
configure: Linux (Netfilter) Transparent Proxy enabled
configure: Using POSIX_V6_LP64_OFF64 build environment
configure: Auth scheme modules built: basic digest ntlm negotiate
configure: Basic auth helpers built: LDAP MSNT NCSA PAM SASL SMB YP DB POP3 getpwnam squid_radius_auth multi-domain-NTLM
configure: NTLM auth helpers built: smb_lm 
configure: Negotiate auth helpers built: squid_kerb_auth
configure: Digest auth helpers built: ldap password
configure: External acl helpers built: ip_user ldap_group session unix_group wbinfo_group
checking sasl/sasl.h usability... no
checking sasl/sasl.h presence... no
checking for sasl/sasl.h... no
checking sasl.h usability... no
checking sasl.h presence... no
checking for sasl.h... no
checking for sasl_errstring in -lsasl2... no
checking for sasl_errstring in -lsasl... no
configure: error: Neither SASL nor SASL2 found
make: *** [debian/stamp-autotools] Error 1
dpkg-buildpackage: error: debian/rules build gave error exit status 2
debuild: fatal error at line 1350:
dpkg-buildpackage -rfakeroot -D -us -uc -b failed

```

---

### Post by cariboo on 2013-05-07
Please don't create multiple threads on the same subject. Thread closed.

---

