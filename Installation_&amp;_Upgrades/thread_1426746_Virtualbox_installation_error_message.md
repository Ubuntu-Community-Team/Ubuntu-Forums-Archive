---
title: "Virtualbox installation error message"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by dinuzz on 2010-03-10
Hi there
I'm installing Sun Virtualbox and get the following error message. The install does not stop or crash, but just don't know what to do about this message:


```

An error occurred while loading or saving configuration information for frontend. Some of your configuration settings may not work properly.

Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-WisHR68kfM: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-WisHR68kfM: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-WisHR68kfM: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-WisHR68kfM: Connection refused)
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://projects.gnome.org/gconf/ for information. (Details -  1: Failed to get connection to session: Failed to connect to socket /tmp/dbus-WisHR68kfM: Connection refused)

```

Installed Ubuntu Desktop 9.10 and most recent Virtualbox.

Thanks for any help.

Cheers

---

### Post by s.fox on 2010-03-10
Hello,

Do you have gconf-defaults-service installed?  If not I would try installing that :)

-Silver Fox

---

### Post by dinuzz on 2010-03-11
ok - two questions:
 
- how do I determine, if this is already installed?
- if it is not, how do I install it?
 
thanks

---

