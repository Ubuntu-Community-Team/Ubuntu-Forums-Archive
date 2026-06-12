---
title: "Best Way Back For Newb From Ibex"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Mr Fredrick on 2008-10-03
Hi All,

When I upgraded from Heron to Ibex yesterday all went well except that on startup the Network Manager always disconnects my wired connection and therefore I can't get on the net or upgrade or modify my system using Synaptic.

My machine is dual boot so I can get on the net using XP.

If its not possible to fix Ibex, what is the quickest way to go back to Heron?

Thanks in advance,

Mr Fred

---

### Post by iponeverything on 2008-10-03
Is there anything showing up in /var/log/syslog when it the connection
gets restarted.

you could also configure the wired connection in /etc/network/interfaces

---

### Post by Ub1476 on 2008-10-03
Probably easier to fix the problem than go back. You need to reinstall Hardy Heron.

---

### Post by Mr Fredrick on 2008-10-03
Attached is the output in my /var/log/syslog file.

---

### Post by iponeverything on 2008-10-03
Humm..

See this thread from kernel trap:
[http://kerneltrap.org/mailarchive/linux-netdev/2008/8/14/2931154/thread](http://kerneltrap.org/mailarchive/linux-netdev/2008/8/14/2931154/thread)
and this from launchpad:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/267830](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/267830)

Do they look like same issues that is affecting you?

At boot choose the 2.6.24 kernel and see if work with that one.


Oct  3 05:14:55 peter-laptop kernel: [   20.752245] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
Oct  3 05:14:55 peter-laptop kernel: [   20.752248] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[...]
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  eth1: Device is fully-supported using driver 'iwl3945'. 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  eth1: driver does not support SSID scans (scan_capa 0x00). 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'eth1'. 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  Deactivating device eth1. 
Oct  3 05:14:59 peter-laptop NetworkManager: <debug> [1222974899.597716] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_mo
del_DVD__RW_GSA_T11N'). 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  Error getting killswitch power: org.freedesktop.Hal.Device.KillSwitch.NotSupported - Access type not supported 
Oct  3 05:14:59 peter-laptop NetworkManager: <info>  Wireless now enabled by radio killswitch

---

