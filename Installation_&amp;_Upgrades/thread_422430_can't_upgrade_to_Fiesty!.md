---
title: "can't upgrade to Fiesty!"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by mandela on 2007-04-25
Hi..I was trying to use this command  gksu "update -manager -c" to upgrade from ubuntu EE to FF but It's giving me this error?
gksu "update-manager -c"
warning: could not initiate dbus
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

I also tried the update manager...its the same story. 

How can I find or know which version of ubuntu I'm using?

---

### Post by Jussi Kukkonen on 2007-04-25
It looks like you do not have dbus (a pretty important part of the system) running. You should try rebooting or restarting dbus:
```
sudo /etc/init.d/dbus restart

```
> 
How can I find or know which version of ubuntu I'm using?
```
 lsb_release -a
```

---

### Post by mandela on 2007-04-25
Thanks for your response. I ran the command lsb_release -a and this is what I got.Looks like I'm update right?

"No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty"

---

