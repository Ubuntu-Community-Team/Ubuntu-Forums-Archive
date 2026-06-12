---
title: "upgrade to Ubuntu Server 12.04 broke Active Directory logins"
date: 2014-05-18
forum: Installation &amp; Upgrades
---

### Post by David_Sheetz on 2014-05-18
After upgrading to Ubuntu Server 12.04 from 11.xx  I can no longer login using ADS on our domain, local users can still login I get "access denied"

I have verified time is correct ,
/etc/network /interfaces is showing proper dns nameservers and DNS search

/etc/samba/smb.conf has proper workgroup and realm information

/etc/krb5.conf has the proper search realms and realm info

sudoers is correct 

I added back to the domain

kinint seems to say I am connected

klist shows my connection

still can not login to console using domain id

any ideas?

---

