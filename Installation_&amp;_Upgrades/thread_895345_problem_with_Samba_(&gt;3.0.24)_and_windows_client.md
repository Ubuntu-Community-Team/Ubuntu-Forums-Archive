---
title: "problem with Samba (&gt;3.0.24) and windows clients"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by XoRDy on 2008-08-20
Hi, I've updated my server from Gutsy to Hardy, and since then I cannot access samba from windows clients, I got this error on /var/log/samba/log. :

[2008/08/20 10:33:55, 2] smbd/sesssetup.c:setup_new_vc_session(1200)
  setup_new_vc_session: New VC == 0, if NT4.x compatible we would close all old resources.


The only fix I found is to downgrade to 3.0.24. versions 3.0.26a and 3.0.28a don't work with windows clients, but all version with with linux clients

This is my smb.conf:

```
[global]
workgroup = mydomainname
server string = %h
os level = 64
preferred master = yes
domain master = yes
local master = yes
wins support = yes
debug level = 2
log file = /var/log/samba/log.%U
max log size = 50000
security = user
encrypt passwords = true
domain logons = yes
logon script = inicio.bat
logon path =
logon home =
dns proxy = yes
time server = yes
socket options = TCP_NODELAY

[netlogon]
   comment = Network Logon Service
   path = /etc/samba/netlogon
   browseable = no
   public = no
   writable = no

[disseny]
   comment = Projectes disseny
   path = /var/sambadir/disseny
   writable = yes
   hide unreadable = yes
   create mode = 0770
   directory mask = 0770
   valid users = @disseny, @practicas
   admin users = @disseny
   force user = disseny
   force group = disseny
   force create mode = 0770
   force directory mode = 0770


[documentacio]
   comment = Documentació varia
   path = /var/sambadir/documentacio
   public = no
   writable = yes
   hide unreadable = yes
   create mode = 0770
   directory mask = 0770
   valid users = @documentacio, @practicas
   admin users = @documentacio
   force user = documentacio
   force group = documentacio
   force create mode = 0770
   force directory mode = 0770
```


The Disseny share didn't work with version greater than 3.0.24, but [documentacion] did work


Any ideas of what's happening here?

---

