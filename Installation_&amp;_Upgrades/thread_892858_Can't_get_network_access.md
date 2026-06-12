---
title: "Can't get network access"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by awam66 on 2008-08-17
Hi, After an update yesterday I find that I can no longer access the net. I also cannot do any admin processes, I get an error message saying I don't have permission to use "sudo". From a root terminal I tried to run the network-admin and got the following message:

(network-admin:5331): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

(network-admin:5331): Liboobs-WARNING **: OobsSession object hasn't connected to the bus, cannot register OobsObject
process 5331: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3280.
This is normally a bug in some application using the D-Bus library.
Segmentation fault

Any ideas what went wrong?

It is hardy I'm running on AMD64

---

### Post by awam66 on 2008-08-18
This has become serious,
Any help please?

Trying to use sudo gives error message 
sudo: must be setuid root

At a loss what to do.

---

