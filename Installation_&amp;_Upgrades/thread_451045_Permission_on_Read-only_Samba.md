---
title: "Permission on Read-only Samba"
date: 2007-05-21
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-05-21
What permission do I need to set so users are able to download files I have uploaded on my Samba?

What I did is I have created a folder under /var/www/samba and configure the following on the /etc/samba/smb.conf:
> 
[Files]
    path = /var/www/samba/
    browseable = yes
    read only = no
    guest ok = no
    valid users = tsoperator
    create mask = 0700
    directory mask = 0700
    force user = nobody
    force group = nogroupFrom the user's browser, they may browse and list all files but when trying to download, it displays the following:

> **Forbidden**

 You don't have permission to access /samba/Database/2007/I070522.mdb on this  server.
   Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at ubuntulinux6.06 Port  80If I browse thru putty, I see these permissions on the file:

-rwx------ 1 nogroup   880640 2007-05-20 09:56 FILE.mdb

How can these file be downloaded even they have these file permission?

---

