---
title: "Alpha 5 in VirtualBox - Cannot start x"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ukblacknight on 2009-09-11
I've been running 9.10 Alpha 5 for a few days in VirtualBox 3.0.6 and performed an upgrade on the guest today.

Since restarting the guest, it now can't start x!

Entering the command: startx gives the following:

```


Fatal server error:
Could not create lock file in /tmp/.tX0-lock


Please consult the The X.Org Foundation support
         at http://wiki.x.org
 for help.

 ddxSigGiveUp: Closing log
giving up.
xinit:  Connection refused (errno 111):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.
xauth:  error in locking authority file /root/.Xauthority

```

There are more error messages above this but I am unable to see them (they scroll past), but they do mention things such as
```

/usr/bin/startx: line 173: cannot create temp file for here-document: Read-only file system

```

I don't have guest additions installed.  I did install it once, but it basically gave me the error I'm posting, so I started from scratch again.  Execpt this time, the error has occured after an update.

---

### Post by ukblacknight on 2009-09-19
Ok, so I installed Alpha 6 the other evening, and that worked fine.  Had an update just now, and it's broken it just like how it was in Alpha 5.  Luckily I took a snapshot before it broke, but I'm wondering - will these breakages happen on my actual machine?  I've no idea why this keeps happening :\

---

