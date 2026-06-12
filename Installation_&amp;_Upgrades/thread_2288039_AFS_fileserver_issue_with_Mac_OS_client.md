---
title: "AFS fileserver issue with Mac OS client"
date: 2015-07-24
forum: Installation &amp; Upgrades
---

### Post by aor2 on 2015-07-24
Hi i have afs running in my ununtu 14.04 i have no issue connecting using windows and ubuntu client but in a mac i have, Every time i will open a file from AFS using finder it will hang spinning beach ball will appear,and waht im going to do is to disconnect the network cable. My installation of afs client is using ticket viewer for kerberos and openafs client

here is my configuration

kerberos mac:

  vim /Library/Preferences/edu.mit.Kerberos
[libdefaults]
     default_realm = TEST.COM
     #kdc_timesync = 1
     ccache_type = 4
     forwardable = true
     proxiable = true
     allow_weak_crypto = true

[realms]
     TEST.TEST.COM = {
         kdc = server.test.com
         admin_server = server.test.com
     }

[domain_realm]
     .test.com = TEST.COM
     test.com = TEST.COM



Openafs:

 edit /var/db/openafs/etc/ThisCell 
test.com
 edit /var/db/openafs/etc/CellServDB and add this line
>test.com
192.168.2.8             # server.test.com



[LIST]
[*]enable "Start AFS at Boot"
[*]Enable AFS Menu
[*]Enable Backgrounder
[*]Enable Use aklog
[*]Enable get credential at login time
[/LIST]


Hope someone can help me on this.

Thanks

---

### Post by aor2 on 2015-08-12
Hi any body uses mac machine as a client? please share your kerberos and afs configuration,,


Thanks a lot..

---

