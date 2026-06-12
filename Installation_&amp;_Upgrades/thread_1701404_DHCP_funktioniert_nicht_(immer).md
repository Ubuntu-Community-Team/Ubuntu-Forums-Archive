---
title: "DHCP funktioniert nicht (immer)?"
date: 2011-03-06
forum: Installation &amp; Upgrades
---

### Post by andimeier on 2011-03-06
When I boot from my freshly installed system (10.04 LTS Server 64bit), there is no network available. Each attempt to obtain a dynamic IP address via DHCP, fails - there is no DHCPOFFER coming back.

This is the output of [COLOR=RoyalBlue]dhclient[/COLOR]:

> Listening on LPF/eth0/00:26:18:f0:1d:43
Sending on   LPF/eth0/00:26:18:f0:1d:43
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.Strange thing, because there is network attached and it works. For instance, if I boot into a live system (via a USB pen drive Ubuntu 10.04), networking is fully functional. The output of [COLOR=RoyalBlue]dhclient [/COLOR]then would be:

> Listening on LPF/pan0/32:1f:97:4d:9e:59
Sending on   LPF/pan0/32:1f:97:4d:9e:59
Listening on LPF/eth0/00:26:18:f0:1d:43
Sending on   LPF/eth0/00:26:18:f0:1d:43
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER of 192.168.178.35 from 192.168.178.1
DHCPREQUEST of 192.168.178.35 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.178.35 from 192.168.178.1
bound to 192.168.178.35 -- renewal in 343891 secondsSo I do not understand: network is availabe but the installed system claims it is not and is unable to connect and unable to receive DHCP offers. Even configuring the system with a static IP does not help. I get no connection.

What could be wrong?

Andi

---

### Post by andimeier on 2011-03-16
Update:

directly after booting the network is unreachable. The tool ethtool reports:
  Link detected: no

Ok, this  means, the problem is on the lowest OSI layers, 1 or 2. Therefore no higher-level services like DHCP etc. are working. Makes sense so far.

Anyway, I discovered how to temporarily work around the problem. Using the following commands, the network gets up:

```
sudo ifdown eth0 (ifdown reports: "send_packet: Network is unreachable")
sudo ifup eth0 -> OK
```Now the interface has successfully received a valid IP, everythings working.

Sometimes I even have to do this twice:

```
sudo ifdown eth0 (ifdown reports: "send_packet: Network is unreachable")
sudo ifup eth0 (ifup reports: "No DHCPOFFERS received.")
sudo ifdown eth0 (ifdown reports: "send_packet: Network is unreachable")
sudo ifup eth0 -> OK
```Does anybody have an idea, what could be the cause for this strange behaviour? After one or two times ifdown/ifup the interface is finally up? And after reboot it is always down initially (I can see it in dmesg) - why?

---

### Post by gordintoronto on 2011-03-16
I don't have any answers. Strange coincidence: yesterday I was fooling around with the new OpenSuse, and it behaved exactly the same. The Live CD connected to the Internet, the installed version did not, but it could access shares on other local computers.

---

### Post by andimeier on 2011-03-16
Incredible! It works now.

What did I do to solve the problem? -> just cut the PC off from any power supply.

In more detail, I did the following:

[LIST]
[*]switched off the PC
[*]**unplugged the power cord**
[*]**unplugged the Ethernet cable**
[*]waited ... waited ... waited (a few minutes)
[*]plugged in powercord and LAN cable again
[*]booted PC
[/LIST]
Now, the network is there, right after the boot. As if there was never a problem.


Don't ask me why. Life is full of mysteries.

Maybe any wise man in this forum can enlighten me how this can be possible ... if not, I'm just happy to have my Ubuntu (plus network) back. :D

---

