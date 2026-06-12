---
title: "Since installing the latest Ubuntu 10.04 kernel I can only boot through failsafeX"
date: 2015-01-04
forum: Installation &amp; Upgrades
---

### Post by gleble on 2015-01-04
Since installing the latest Ubuntu 10.04 kernel I can only boot through failsafeX

The log says:

Fatal server error: Sever already active for display 0

Then it advises me to remove tmp/.x0-lock  which I did

also says

(WW) xf86 CloseConsole KDSETMODE  failed: Bad file descriptor
(WW) xf86 CloseConsole VT_GETMODE  failed: Bad file descriptor
(WW) xf86 CloseConsole VT_GETSTATE  failed: Bad file descriptor

Any ideas would be appreciated

---

### Post by grahammechanical on 2015-01-04
This is an installation of Ubuntu Server, is it not? Please confirm. Ubuntu 10.04 desktop edition reached end of life May 2013.

Regards.

---

### Post by MAFoElffen on 2015-01-04
Not really. The whole error the OP is describing is usually like this:
```

Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.X0-lock
    and start again.

```
Where the error is from XServer, where X session 0 has a temp file open and the file is locked, therefore it thinks that graphics session either active (running), being used by another user, other than current... or that file may be left held in a locked state by an error. This error also occurs when a user tries to start X as root, or change an X related setting as root (another user), when that X session is still active. Therefore being denied, because. of permissions.

If they installed something and it gets this error, then whatever they were trying to do, previous to this error, tried to do something with X, and was deinied. So this error can come up if a UserID from a program, doesn't have permissions... so:
```

OffendingID=(<To be determined>)
[ -z "$DISPLAY" ] && startx && {sleep 5; DISPLAY=0:0 setsid $OffendingID; }

```
Where "OffendingID" would have to be researched and found in the sys log... At logiin (the graphical login) that OffendingID might be the supplied UserName... So the OP, in this instance should replace that first command with this (substituting "[COLOR=#ff0000]userName[/COLOR]" with his own UserID:
```

[ -z "$DISPLAY" ] && startx && {sleep 5; DISPLAY=0:0 setsid [COLOR=#ff0000]userName[/COLOR] }

```
When a OP tells me they installed something, and then when they boot, they got an X permissions denial message... When they install something, it is using root permission for that... Sometimes the /home/userName/.Xauthority file get corrupted or most usually, the permissions of that get changed to root instead of the user. Diagnose with 
```

ls -l /home/userName/.Xauthority

```
and insure it says userName (your own) root... and not root root... If it says "... root root", I'll explain another way to correct that...

Question to the OP is, why 10.04 LTS, which is now not supported and past it's End Of Life (EOL)? Why not something supported?

---

