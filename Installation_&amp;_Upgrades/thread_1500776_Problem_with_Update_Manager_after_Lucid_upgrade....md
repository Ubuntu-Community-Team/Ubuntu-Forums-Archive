---
title: "Problem with Update Manager after Lucid upgrade..."
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by chaeron on 2010-06-03
I managed to upgrade my laptop from Karmic to Lucid using the Alternative ISO. But now when I run update manager (gksudo update-manager) and then tell it to update packages, I these error messages:

```

warning: could not initiate dbus
...
glib.GError: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details - 1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

The update notifier seems to have issues which I presume are related. 

However, if I do a sudo su - and then start update-manager, it will download and install packages just fine.

Very strange. Any ideas on how to fix this?

---

### Post by chaeron on 2010-06-03
Solved it....turns out there was a permissions problem on the file:

/etc/apt/apt.conf.d/99synaptic

Once I added ugo+r permissions, like all the other files in there, it resolved the problem.

Wonder how that happened?  Gremlins! Ugh!

---

