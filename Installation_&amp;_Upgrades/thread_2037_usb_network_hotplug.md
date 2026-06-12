---
title: "usb network hotplug"
date: 2004-10-25
forum: Installation &amp; Upgrades
---

### Post by vulpes on 2004-10-25
I'm trying to connect my Sharp Zaurus to Ubuntu. When I plug it in, usbnet gets loaded and the Zaurus found. However, I cannot figure out how to make 'ifup usb0' with my parameters in /etc/network/interfaces happen automatically. I have the following:

iface usb0 inet static
    address 192.168.129.1
    pointopoint 192.168.129.201
    netmask 255.255.255.255

(based on search for 'Debian Zaurus usb0'). I restarted hotplug, but maybe I'm missing something with the new dbus / udev stuff or ...
Thanks.

---

