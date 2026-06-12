---
title: "Cisco VPN client not working since kernel upgrade"
date: 2008-10-26
forum: Installation &amp; Upgrades
---

### Post by geezerone on 2008-10-26
Hi

Since upgrading from ...19 to 2.6.24-21 kernel my cisco vpn client isn't working.

I have uninstalled (sudo ./vpn_uninstall) but left profiles to no avail.

The first error was : ```
sudo vpnclient connect vpnsite
Cisco Systems VPN Client Version 4.8.01 (0640)
Copyright (C) 1998-2007 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.24-21-generic #1 SMP Mon Aug 25 16:57:51 UTC 2008 x86_64
Config file directory: /etc/opt/cisco-vpnclient

Could not attach to driver. Is kernel module loaded?
The application was unable to communicate with the VPN sub-system
```I managed to load module via: ```
sudo /etc/init.d/vpnclient_init start
``````
sudo ln -s /etc/init.d/vpnclient_init /etc/rc2.d/S85vpnclient_init
``` - to make module load after reboot.

But although I can from what it seems, establish a vpn connection, I am unable to ping or connect to any devices on the remote site :confused:

Help appreciated.

---

### Post by georgew on 2009-03-08
You must rebuild the kernel module after upgrading the kernel.

The loadable module has to be built using the header files of the currenly running kernel to load properly.  You must rebuild it each time you upgrade your kernel.

In your directory where you originally unpacked the vpn client, go re-run the "vpn_install" script.  That script will probe the kernel, and then prompt you for the path of the kernel headers, the prompt should have a correct guess, so you should be able to just hit return there.  It will then rebuild the driver based on the new kernel headers, and load it for you.

You should be good to go after that!


George

---

