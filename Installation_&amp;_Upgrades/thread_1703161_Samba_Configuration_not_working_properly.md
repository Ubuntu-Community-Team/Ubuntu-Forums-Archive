---
title: "Samba Configuration not working properly"
date: 2011-03-08
forum: Installation &amp; Upgrades
---

### Post by kamran.khan on 2011-03-08
I have configured Samba Server properly according to the configuration manual given 
by Ubuntu. I am able to access Ubuntu PC from Windows 7. Folder is also accessible by
giving full rights to everyone. But when I am trying to give rights to some specific samba
user, i am unable to access. At the bottom of the login window in Windows Access Denied 
appears, and when i entered username/password it is unable to authenticate. Kindly give me some solution
of this problem. I am using Samba Desktop Edition 10.10. I have followed the following
configuration for file share.

[share]
    comment = Ubuntu File Server Share
    path = /srv/samba/share
    browsable = yes
    guest ok = yes
    read only = no
    create mask = 0755

---

