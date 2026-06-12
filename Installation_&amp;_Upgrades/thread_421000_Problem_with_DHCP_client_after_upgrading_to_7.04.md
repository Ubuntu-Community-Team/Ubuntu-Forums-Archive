---
title: "Problem with DHCP client after upgrading to 7.04"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by mikaelstaldal on 2007-04-24
Since upgrading to Ubuntu 7.04 I got problems with the DHCP client. I get a five minutes delay before getting my IP address. The problem occurs both at boot and when doing "ifdown eth0" and "ifup eth0". I have a normal PC with Ethernet, no wireless.

From /var/log/daemon.log:
```

Apr 24 09:40:42 ws-136 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 24 09:40:45 ws-136 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 24 09:40:52 ws-136 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Apr 24 09:41:06 ws-136 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
Apr 24 09:41:13 ws-136 dhclient: No DHCPOFFERS received.
Apr 24 09:41:13 ws-136 dhclient: No working leases in persistent database - sleeping.
Apr 24 09:41:13 ws-136 ntpdate[6653]: can't find host ntp.ubuntu.com 
Apr 24 09:41:13 ws-136 ntpdate[6653]: no servers can be used, exiting
Apr 24 09:44:15 ws-136 dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Apr 24 09:44:15 ws-136 dhclient: DHCPOFFER from 10.0.0.1
Apr 24 09:44:15 ws-136 dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Apr 24 09:44:15 ws-136 dhclient: DHCPACK from 10.0.0.1
Apr 24 09:44:15 ws-136 dhclient: bound to 10.0.0.136 -- renewal in 20708 seconds.

```

According to the sever's log, the first DHCPDISCOVER packets are not sent. Nothing shows up in the server log before 09:44.

When I used Ubuntu 6.10 it worked without problems.

I guess I got this problem because I uninstalled NetworkManager. But I don't want NetworkManager (since it seems unnecessary for me). I just want to get it to work as in 6.10 without NetworkManager.

---

