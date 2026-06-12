---
title: "config samba login directory"
date: 2006-12-21
forum: Installation &amp; Upgrades
---

### Post by moonhk on 2006-12-21
Using Window login ubuntu machine. The share directory is /tmp . How to change/config  to other directory ?

---

### Post by darrenm on 2006-12-21
Edit /etc/samba/smb.conf (its very well commented.) then
```
sudo /etc/init.d/samba restart
```

when you have finished making the changes.

---

### Post by moonhk on 2006-12-22
in config file , Just below section have path=/tmp.


[printers]
   comment = All Printers
   browseable = no
   path = /tmp
   printable = yes
   public = no
   writable = no
   create mode = 0700


I try to updated same problem. In windows just located on /tmp directory.

# The following setting only takes effect if 'domain logons' is set
# It specifies the location of a user's home directory (from the client
# point of view)
;   logon drive = H:
;   logon home = \\%N\%U
logon home = \home\shared

---

