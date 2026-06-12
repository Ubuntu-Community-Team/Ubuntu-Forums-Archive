---
title: "Samba shares broken by LTSP/Xubuntu?"
date: 2006-08-29
forum: Installation &amp; Upgrades
---

### Post by Jose Catre-Vandis on 2006-08-29
Weird problem, can't figure out what has changed?

On my lan, I have 6 PC's (all Ubuntu)
One of them is/was an Ubuntu server LAMP install
This serves up websites using apache/php
I set up some samba shares from the server to my own PC
and changed permissions so that I could read and write to
these shares. This worked fine.

I then installed xubuntu-desktop on the server, followed up by
LTSP. This installation went well, and I was able to PXE boot into the LTSP server 
(using a distinct IP range for the LTSP dhcp server, distinct from my LAN router) 
from machines on the LAN.

However, when I went back to load the samba shares, I got an ACCESS DENIED error:
```
"tree connect failed: ERRDOS - ERRnoaccess (Access denied.)
SMB connection failed"
``` 
So I checked smb.conf, all the passwords, checked shares, logins and users, 
and nothing appears to have changed. 
The shares are available in a PXEboot client. 
But they refuse to mount on my PC.

Can anyone point me in the direction of a cure?

---

### Post by Jose Catre-Vandis on 2006-08-29
SOLVED!

Finally, found what was needed

For some reason, the samba permissions requirements changed, and for my shared folders I needed to add the line "valid users = ", as in:

```
[Group]
  comment = Group Folder
  path = /home/group
  public = yes
  writable = yes
  
  valid users = system_username1 system_username2

  create mask = 0700
  directory mask = 0700
  force user = nobody
  force group = nogroup
```

Don't know why , all worked perfectly OK without it before. Anyway, this might help someone else along the way.

---

