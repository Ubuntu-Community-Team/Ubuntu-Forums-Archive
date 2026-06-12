---
title: "Can't access &quot;Windows Network&quot; though Nautilus"
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Chrisn02 on 2010-03-16
Hi, I'm trying to access some file shares another machine using windows file shares however the following message appears after a long wait trying to open "Windows network" in Nautilus.
```
Unable to mount location
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply.  Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

This is a clean install using lucid netbook remix inside a VM (VMWare player).

Only thing I've done to it is install winbind and add wins to /etc/nsswitch.conf  (added before dns).

I must be missing something but don't know what yet.

Any ideas?

---

### Post by cariboo on 2010-03-16
It seems to be a problem with gvfs, the bug has been sent upstream to the gvfs maintainer.

**Edit** It is actually a bug in gvfsd-smb

---

### Post by katie-xx on 2010-03-16
> **cariboo907 said:**
> It seems to be a problem with gvfs, the bug has been sent upstream to the gvfs maintainer.

Thanks for the heads up. Ive found something similar.

Kate

---

### Post by Chrisn02 on 2010-03-17
Thanks for the info.  
I think I've now managed to find the bug in launchpad your talking about.
[bug 532024]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/532024")

---

