---
title: "USB Pendrives Won't Mount After Upgrade"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by trey333om on 2008-11-23
After upgrading to 8.10, whenever I try to plug in any USB thumb/pen drive, it gives me a:

[INDENT][I]Unable to mount UBUNTU-USB

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/I][/INDENT]

Portable hard drives work fine. The same thumbdrives (notice the plural) work perfectly in my two other computers running Ibex.

Tried restarting HAL and DBus, but no help...:

    *sudo /etc/init.d/hal restart && sudo /etc/init.d/dbus restart*

Any ideas?

---

