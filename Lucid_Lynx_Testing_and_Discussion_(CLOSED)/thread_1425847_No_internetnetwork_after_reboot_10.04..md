---
title: "No internet/network after reboot 10.04."
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jeeperscreepers on 2010-03-09
**Fresh Install of Ubuntu 10.04 alpha 3. Everything stock other than changes mentioned. As of right now it keeps trying to connect but get's nowhere. Other computers can connect through this cable. Card does appear to be connected. Is this an ipv6 issue?**
**earl@earl:~$ dmesg | grep eth**
[ 2.581710] eth0: RealTek RTL8139 at 0xd800, 00:15:f2:05:e9:bf, IRQ 17
[ 13.557773] eth0: link down
[ 13.557878] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 345.446631] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[ 345.446674] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 345.551097] eth0: link down
[ 356.344007] eth0: no IPv6 routers present

**earl@earl:~$ ping 192.168.1.1**
connect: Network is unreachable

**earl@earl:~$ ifconfig**
eth0 Link encap:Ethernet HWaddr 00:15:f2:05:e9:bf
inet6 addr: fe80::215:f2ff:fe05:e9bf/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:168 (168.0 B)
Interrupt:17 Base address:0xd800

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:720 (720.0 B) TX bytes:720 (720.0 B)

**I then tried the following**
sudo ifconfig eth0 <ip_address> up
sudo route add default gw <gateway_address>
ping -c3 <gateway_address>
[B]
dmesg output:[/B]
[12922.306375] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[12922.413398] eth0: link down
[12927.161694] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[12927.266034] eth0: link down
[12959.600165] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[12959.704319] eth0: link down
[12982.299918] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[12982.402929] eth0: link down
[13407.683997] eth0: link up, 10Mbps, half-duplex, lpa 0x0000
[13407.788436] eth0: link down

[B]Okay, i've disabled ip6 and all that. Through grub.
I now no longer get the ipv6 error.
I still can not connect. A minute ago it said it could find a connection.
On another note, my /etc/network/interfaces doesn't have an eth0 in it only:[/B]
auto lo
iface lo inet loopback

[B]Does this mean my ethernet card is not hooked up right?
I quoted that out and replaced it with:[/B]
auto eth0
iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

[B]Restarted networking, no results. Restarted computer, No Results.

On restart firefox crashed when i first tried to open it, window formed but dissipated. Pinging the router resulted in Destination Host unreachable.[/B]

Pretty much a complete newb, Usually i would have to use ethtool to adjust my card settings. With ubuntu 10.04, ethtool not available but card appears to be using the right settings on it's own. 10mb/s half duplex.

---

### Post by jeeperscreepers on 2010-03-09
Can give any details required. Might be something basic im doing wrong her but i just can't see it.

---

### Post by i22yb on 2010-04-04
Same problem here.  Upgraded from Karmic to Lucid and after reboot, wired network is dead.  If I plug in a wireless USB adapter I can connect just fine.  Don't know what to adjust, if anything, to get the wired to work now.  Never had a problem with it until the upgrade.

---

### Post by i22yb on 2010-04-04
OK, I just stumbled across a fix for mine.  Edited the wired connection settings: IPV6 tab, set "Method" = Ignore.  Presto!  Wired connection works again.

---

