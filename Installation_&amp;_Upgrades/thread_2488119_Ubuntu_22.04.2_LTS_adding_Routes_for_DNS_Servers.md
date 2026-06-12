---
title: "Ubuntu 22.04.2 LTS adding Routes for DNS Servers"
date: 2023-06-23
forum: Installation &amp; Upgrades
---

### Post by brettroderick on 2023-06-23
Problem occurring after:
-Ubuntu 22.04.2 LTS upgraded from Ubuntu 18.04.6 LTS
-Ubuntu 22.04.2 LTS upgraded from Ubuntu 20.04.6 LTS


Systems are:
--Ubuntu Servers are on Azure VM running OpenVPN Access Server
--Ubuntu Servers on physical servers running OpenVPN Client


Problem:
After upgrading to Ubuntu 22.04.2 LTS, Ubuntu is creating IP Routes for DNS Servers on different subnets breaking VPN routes.


Example:
Destination Gateway Genmask Flags Metric Ref Use Iface
8.8.8.8 92.168.222.2 255.255.255.255 UGH 100 0 0 enp1s0
192.168.111.4 192.168.222.2 255.255.255.255 UGH 100 0 0 enp1s0


As a workaround:
-I can remove DNS Servers from different subnets which resolves the problem.
-I can manually remove routes and the systems work correctly.


I tried to:
Edit all found network files and add:
[Network]
DNSDefaultRoute=false


This had no effect; routes are still added.
I need to disable this new feature. Any help would be grateful.

---

### Post by MAFoElffen on 2023-06-23
This is a duplicate thread to your original first post in the General Help section two days ago, right? ([https://ubuntuforums.org/showthread.php?t=2488047](https://ubuntuforums.org/showthread.php?t=2488047))

That is not allowed and I am sure that a Moderator will close one of the two threads...

---

