---
title: "VPN port not able to open on server."
date: 2016-02-07
forum: Installation &amp; Upgrades
---

### Post by Elangovan_N on 2016-02-07
Hello,
I have Installed openvpn on ubuntu server as per following link : [https://help.ubuntu.com/14.04/serverguide/openvpn.html](https://help.ubuntu.com/14.04/serverguide/openvpn.html).
After installation VPN Client is not able to connect to vpnserver. When i telnet on sever it's saying " Unable to connect to remote host: Connection refused "
Please help me How to i check openvpn working or not and why telnet is not opening port 1194 on server.

[email]root@xxx.xxx.xxx.xxx[/email]:/etc/openvpn# ifconfig tun0
tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:10.8.0.1  P-t-P:10.8.0.2  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


**root@xxx.xxx.xxx.xxx:/etc/openvpn# telnet localhost 1194**
**Trying 127.0.0.1...**
**telnet: Unable to connect to remote host: Connection refused**
[email]root@xxx.xxx.xxx.xxx[/email]:/etc/openvpn#

Thanks,
Elangovan N

---

