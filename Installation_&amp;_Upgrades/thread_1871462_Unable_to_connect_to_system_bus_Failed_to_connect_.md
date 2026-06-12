---
title: "Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus"
date: 2011-10-28
forum: Installation &amp; Upgrades
---

### Post by abadr on 2011-10-28
Hi,

I have a very basic Ubuntu Server 11.04 LVM encrypted installation running Samba server with no GUI to 11.10. Now the network doesn't start giving me the error:
```
Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: connection refused
```
I found similar problems discussed on the net but they also involved not being able to log in and the display manager not working. I can log in and have no display manager or GUI installed.
How can fix this?

Thanks
A.B.

---

### Post by hansdown on 2011-10-28
Hi, abadr.

It is a bug, that is being worked on.

[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441](https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/811441)

---

