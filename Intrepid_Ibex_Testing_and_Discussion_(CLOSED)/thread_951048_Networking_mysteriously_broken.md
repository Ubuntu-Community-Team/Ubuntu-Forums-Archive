---
title: "Networking mysteriously broken"
date: 2008-10-17
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mjpolifka on 2008-10-17
I installed 8.10 in VirtualBox earlier this week, and everything worked great.  However after leaving it offline for a few days I fire it up and it won't connect to my wired network (dhcp).  I went into network-manager and changed it to static, ifconfig says its up with all the right addresses but I can't ping my gateway (or any other computer on the network, and it's not found in nmap).  I uninstalled network-manager and configured it with /etc/network/interfaces then restarted networking and again it shows correctly in ifconfig but can't ping my gateway.  I rolled back to a snapshot I took just after installing all updates with the same results. :confused:

VirtualBox running on an 8.04 host, using Host Interface networking.  Three other VMs use the same type of networking and all are functioning properly.

Let me know if you want any system/log output, I'm not sure which are applicable.

EDIT:
dhclient does not bring up the interface.
Disabled IPv6 with no changes
Nothing about it in dmesg
Can ping my own IP (eth0's IP, not the loopback), just not my gateway or any other computer on the network

EDIT2:
Started a new VM and installed fresh from the .iso; it won't connect either
My Mandriva and Centos VMs work just fine

---

### Post by mjpolifka on 2008-10-21
Well I fixed my Ubuntu 8.10 networking, but in the process broke my other VMs.  On a hunch I reset my networking and brought up and down my bridge and taps with the scripts written on [**this page**]("https://help.ubuntu.com/community/VirtualBox").

I brought up my 8.10 VM and it was working again, but about an hour later I brought up my CentOS VMs and now their networking doesn't work.  Any thoughts?

---

### Post by btdown on 2008-10-21
My networking mysteriously broke with yesterdays updates. Will try to fix it.

---

