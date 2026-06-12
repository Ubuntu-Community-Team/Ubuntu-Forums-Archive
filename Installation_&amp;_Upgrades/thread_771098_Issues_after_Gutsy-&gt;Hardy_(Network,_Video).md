---
title: "Issues after Gutsy-&gt;Hardy (Network, Video)"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by homeofpoe on 2008-04-27
System: Gateway MX6453

First issue: the video resolution was stuck at 800x600. I reconfigured the xorg, and eventually, after a couple of restarts and tweaking, it displays properly (at one point, the desktop was just... black). Once that was done, though, everything video-related seems slow -- dragging a window across the screen shows the window stuttering slowly across, definitely behind the cursor. I'm unsure of how to fix this. The resolution and desktop are finally fine, it's just the rate everything seems to happen at: choppy.

Second issue: I used the update-manager to upgrade to Hardy Heron. It installed fine, though took a while. After a restart, the network doesn't work at all. When originally installing Ubuntu the first time (Gutsy), I had to use the b43-fwcutter and fiddle with it until it finally worked...but it did. Now, it doesn't work. Under the Hardware Drivers, I couldn't click/download the listed one -- instead, downloaded a .deb from the other computer and brought it over, installed, seemingly fine. But there's still no internet. Using the network manager, trying to "Configure" the network results in: "The interface does not exist."

So I tried some troubleshooting, here's my efforts at discovery:

(sorry for how much is included... not sure what would be useful and not!)

'sudo ifconfig'
```
[sudo] password for user: 
eth1      Link encap:Ethernet  HWaddr 00:e0:b8:b8:b4:2e  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9000 (8.7 KB)  TX bytes:9000 (8.7 KB)
```

Odd. No eth0 (the wireless interface on this laptop).


'sudo ifdown eth0'
```
RTNETLINK answers: No such process
There is already a pid file /var/run/dhclient.eth0.pid with pid 19186
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:14:a5:ca:79:71
Sending on   LPF/eth0/00:14:a5:ca:79:71
Sending on   Socket/fallback
DHCPRELEASE on eth0 to 192.168.1.1 port 67
send_packet: Network is unreachable
send_packet: please consult README file regarding broadcast address.
SIOCSIFFLAGS: No such file or directory
```

Then, 'sudo ifup eth0'
```
SIOCSIFFLAGS: No such file or directory
There is already a pid file /var/run/dhclient.eth0.pid with pid 134519072
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wmaster0: unknown hardware address type 801
SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:14:a5:ca:79:71
Sending on   LPF/eth0/00:14:a5:ca:79:71
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
RTNETLINK answers: Network is down
run-parts: /etc/network/if-up.d/avahi-autoipd exited with return code 2
```

An 'iwconfig'
```
lo        no wireless extensions.

eth1      no wireless extensions.

wmaster0  no wireless extensions.

eth0      IEEE 802.11g  ESSID:"ACT"  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


'sudo lshw -C network'
```
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 14
       serial: 00:e0:b8:b8:b4:2e
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 link=no module=sky2 multicast=yes port=twisted pair
  *-network
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: eth0
       serial: 00:14:a5:ca:79:71
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g
```

---

### Post by homeofpoe on 2008-04-27
Ah. Forgot to say how we configured it!

I followed these instructions:

[http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation](http://linuxwireless.org/en/users/Drivers/b43#firmwareinstallation)


Involved these files:
b43-fwcutter-011.tar.bz2
broadcom-wl-4.80.53.0.tar.bz2

---

### Post by homeofpoe on 2008-04-27
'sudo iwlist eth0 scan'
```
eth0    Interface doesn't support scanning : Network is down
```

---

### Post by Roti on 2008-06-04
Hi!

 Same problem here. No wired internet after network upgrade. I have to use my window$ to post here.

Do you have any solution already?

Thanx


Roti

---

