---
title: "Help - no internet connection when upgrading from Hardy to Karmic"
date: 2010-04-17
forum: Installation &amp; Upgrades
---

### Post by Al B on 2010-04-17
I did an upgrade over the internet and on rebooting after it had completed there was no internet connection.  I wired in an ethernet cable and although I can access the router and ping another machine on the network, there is no internet connection. Any advice would be welcome.

---

### Post by Greg Xix on 2010-04-17
I know this sounds remedial, but try clicking on the Internet connection icon in your trey and selecting eth0 or eth1...or whatever is there. I have this problem from time to time as well.

Also, you could powerdown the router and modem and do a cold shutdown-reboot.

---

### Post by Al B on 2010-04-17
When I click on network connections manager I seem to have three connections

ifupdown(eth0)
ifupdown(eth1)
ifupdown(eth2)

The actual connection is eth2

Clicking on it has no effect

---

### Post by Greg Xix on 2010-04-17
> **Al B said:**
> When I click on network connections manager I seem to have three connections

ifupdown(eth0)
ifupdown(eth1)
ifupdown(eth2)

The actual connection is eth2

Clicking on it has no effect


I assume you tried eth0 and eth1 as well. Did you try unplugging the router and modem and cold rebooting?

Unless you have multiple NIC cards or connections, you should only have 1 and that should be eth0. That goes for every computer you have regardless of how many PC's are connected to the router. I know because I frequently have 2 or 3 computers connected to 1 hub and they are all eth0 connections.

You should probably delete the file containing all 3 and rebooting which will automatically rebuild a fresh list. I can show where the file is. If all else fails.

---

### Post by Al B on 2010-04-17
> **Greg Xix said:**
> I assume you trued eth0 and eth1 as well. Did you try unplugging the router and modem and cold rebooting?

Unless you have multiple NIC cards or connections, you should only have 1 and that should be eth0. That goes for every computer you have regardless of how many PC's are connected to the router. I know because I frequently have 2 or 3 computers connected to 1 hub and they are all eth0 connections.

You should probably delete the first 2. I can show you how to do all of them if you wish

I tried cold rebooting and it had no effect. I only have 1 network card in the machine.   Therefore I would appreciate instructions on how to delete the other two connections.

---

### Post by Greg Xix on 2010-04-17
> **Al B said:**
> I tried cold rebooting and it had no effect. I only have 1 network card in the machine.   Therefore I would appreciate instructions on how to delete the other two connections.

Are you using Kubuntu? I know how it works via Gnome-Ubuntu. So I hope the file structure is the same. 

1. run *sudo nautilus* in a terminal

2. in Location: */etc/udev/rules.d*

3. delete the *70-persistent-net.rules* file

4. reboot

5. Once its rebooted, the file should be remade a lot cleaner(take a peek or back up before deleting, although I never do)

6. while rebooting the PC, be sure to reset that modem and router. I always unplug them

PM if you'd like and we can share IM info if that doesnt work.

---

### Post by Al B on 2010-04-17
> **Greg Xix said:**
> Are you using Kubuntu? I know how it works via Gnome-Ubuntu. So I hope the file structure is the same. 

1. run *sudo nautilus* in a terminal

2. in Location: */etc/udev/rules.d*

3. delete the *70-persistent-net.rules* file

4. reboot

5. Once its rebooted, the file should be remade a lot cleaner(take a peek or back up before deleting, although I never do)

6. while rebooting the PC, be sure to reset that modem and router. I always unplug them


PM if you'd like and we can share IM info if that doesnt work.

Followed the above but the original configuration appears to appear on rebooting.  Will PM.

---

### Post by Iowan on 2010-04-17
Do you have your interfaces defined in */etc/network/interfaces*? If so, try commenting them out (leave the two lines defining "lo") and reboot/restart.

---

