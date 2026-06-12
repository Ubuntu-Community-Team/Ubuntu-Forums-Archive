---
title: "Wireless isn't connecting to AP - DHCP?"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SilvaRizla on 2009-08-02
I'm on a fresh install of Karmic x64 using a Belkin N Wireless F56D8053 on rt2800usb drivers found here: [http://forums.remote-exploit.org/bt4beta-working-hardware/23407-alfa-awus050nh-rt2x00-compat-wireless.html](http://forums.remote-exploit.org/bt4beta-working-hardware/23407-alfa-awus050nh-rt2x00-compat-wireless.html) (current ralink drivers don't compile on this kernel, and other "modded" versions don't work)

The drivers seem to have installed correctly, I can put the card into monitor mode without issue and can even inject packets.  I can't however connect to my AP which is open system, no encryption, nor any other AP.  I can see available wireless networks on both knetworkmanager and wicd.  I am currently using wicd and when I try to connect I get "Obtaining IP Address" and then a short while later, "Unable to obtain IP address".

I'm having to boot in to Vista so to save time here is everything I thought someone may need to get to the bottom of this, there's a lot but that might be a good thing:

Output of iwconfig:

> dave@Desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"D-Link"
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:0F:3D:65:4E:FE
          Tx-Power=12 dBm
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on


Output of ifconfig:

> 
dave@Desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:18:8b:5c:b9:21
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:14700 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10076 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:16532127 (16.5 MB)  TX bytes:1599819 (1.5 MB)
          Interrupt:19

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:169 errors:0 dropped:0 overruns:0 frame:0
          TX packets:169 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:14074 (14.0 KB)  TX bytes:14074 (14.0 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:75:3b:e3:98
          inet6 addr: fe80::222:75ff:fe3b:e398/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5081 (5.0 KB)  TX bytes:7100 (7.1 KB)

wlan0:avahi Link encap:Ethernet  HWaddr 00:22:75:3b:e3:98
          inet addr:169.254.9.66  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1


Output of netstat -rn

> 
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlan0
0.0.0.0         0.0.0.0         0.0.0.0         U         0 0          0 wlan0


Output of dhclient wlan0

> 
sudo dhclient wlan0
There is already a pid file /var/run/dhclient.pid with pid 5361
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:22:75:3b:e3:98
Sending on   LPF/wlan0/00:22:75:3b:e3:98
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Output of lsusb:

> 
Bus 002 Device 005: ID 413c:2010 Dell Computer Corp.
Bus 002 Device 004: ID 413c:1003 Dell Computer Corp.
Bus 002 Device 002: ID 0461:4d15 Primax Electronics, Ltd Dell Optical Mouse
Bus 002 Device 003: ID 045e:00f5 Microsoft Corp. LifeCam VX-3000
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 007: ID 050d:815c Belkin Components
Bus 001 Device 005: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0644:0200 TEAC Corp.


Some output of dmesg

> 
[ 1673.004028] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.                                                                            
[ 1674.917018] wlan0: no IPv6 routers present                                                                                                                     
[ 1677.572019] eth0: no IPv6 routers present                                                                                                                      
[ 1723.742188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1723.940034] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1724.140027] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)                                                                                                
[ 1724.340026] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out                                                                                              
[ 1777.804098] b44: eth0: Link is down.                                                                                                                           
[ 1785.804181] b44: eth0: Link is up at 100 Mbps, full duplex.                                                                                                    
[ 1785.804188] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[ 1802.803188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1803.001040] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1803.200031] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)                                                                                                
[ 1803.401036] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out                                                                                              
[ 1809.441217] b44: eth0: powering down PHY                                                                                                                       
[ 1809.455769] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       
[ 1809.770339] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                                      
[ 1809.771189] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                

[b][ 1809.968061] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1809.970853] wlan0 direct probe responded                                                                                                                       
[ 1809.970859] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[ 1809.972445] wlan0: authenticated                                                                                                                               
[ 1809.972483] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                                 
[ 1809.974578] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)                                                                            
[ 1809.974583] wlan0: associated                                                                                                                                  
[ 1809.983831] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready                                                                                                 
[/b]

^^^^^^^^^ These fall off so quick I wasn't aware it connected, IP address error still came up on wicd


[ 1812.816186] b44: eth0: Link is up at 100 Mbps, full duplex.
                                                                                               
[ 1812.816194] b44: eth0: Flow control is off for TX and off for RX.                                                                                              
[ 1812.816906] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready                                                                                                  
[ 1813.017034] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.                                                                            
[ 1820.476017] wlan0: no IPv6 routers present                                                                                                                     
[ 1823.384018] eth0: no IPv6 routers present                                                                                                                      
[ 1874.349189] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1874.549030] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1874.749024] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)                                                                                                
[ 1874.949026] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out                                                                                              
[ 1887.341333] ADDRCONF(NETDEV_UP): wlan0: link is not ready                                                                                                      
[ 1887.343190] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)                                                                                                
[ 1887.388240] b44: eth0: powering down PHY                                                                                                                       
[ 1887.513329] ADDRCONF(NETDEV_UP): eth0: link is not ready                                                                                                       

[b][ 1887.541092] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)                                                                                                
[ 1887.544328] wlan0 direct probe responded                                                                                                                       
[ 1887.544340] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)                                                                                              
[ 1887.557188] wlan0: authenticated
[ 1887.557224] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)
[ 1887.571712] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)
[ 1887.571720] wlan0: associated
[/b][ 1887.585963] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

[ 1890.804180] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 1890.804187] b44: eth0: Flow control is off for TX and off for RX.
[ 1890.804889] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[ 1897.640014] wlan0: no IPv6 routers present
[ 1899.004032] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.
[ 1901.616016] eth0: no IPv6 routers present
[ 2931.804096] b44: eth0: Link is down.
[ 2932.409211] b44: eth0: powering down PHY
[ 2932.424108] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2942.555188] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 2942.752029] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)
[ 2942.953038] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)
[ 2943.153026] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out
[ 2961.697207] b44: eth0: powering down PHY
[ 2961.711062] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 2962.021348] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 2962.027441] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 2962.030836] wlan0 direct probe responded
[ 2962.030843] wlan0: authenticate with AP 00:0f:3d:65:4e:fe (try 1)
[ 2962.032564] wlan0: authenticated
[ 2962.032597] wlan0: associate with AP 00:0f:3d:65:4e:fe (try 1)
[ 2962.034692] wlan0: RX AssocResp from 00:0f:3d:65:4e:fe (capab=0x421 status=0 aid=1)
[ 2962.034697] wlan0: associated
[ 2962.044808] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2972.505015] wlan0: no IPv6 routers present
[ 2977.005058] No probe response from AP 00:0f:3d:65:4e:fe after 200ms, disconnecting.
[ 6411.200686] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 1)
[ 6411.400032] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 2)
[ 6411.600023] wlan0: direct probe to AP 00:0f:3d:65:4e:fe (try 3)
[ 6411.800028] wlan0: direct probe to AP 00:0f:3d:65:4e:fe timed out


my /etc/network/interfaces file

> 

auto lo
iface lo inet loopback
auto wlan0
iface wlan0 inet dhcp


If I plug an ethernet cable in, it works fine, but not with wireless.  Any ideas anyone?

---

### Post by fifth on 2009-08-02
[karmic kde networkmanager-plasma-applet not connecting wireless]("http://ubuntuforums.org/showthread.php?t=1202434")

---

### Post by SilvaRizla on 2009-08-02
I think that is a seperate issue it only seems to affect the network-manager backend, which I don't have as I'm using wicd.  For info it affects both in my case

thanks anyway though

---

### Post by fifth on 2009-08-02
> **SilvaRizla said:**
> I think that is a seperate issue it only seems to affect the network-manager backend, which I don't have as I'm using wicd.  For info it affects both in my case

thanks anyway though

Yeah sorry your right. Just installed wicd here and seems to be working.

---

### Post by decoherence on 2009-08-02
I have this problem with the latest updates, both with wicd and networkmanager.

the old fashioned way still works, though, once you stop wicd/networkmanager and the wpa_supplicant daemon from running. i'm currently doing it by manually running wpa_supplicant to associate then dhclient to get an IP address. /etc/network/interfaces could be set up to do the same thing.

---

### Post by SilvaRizla on 2009-08-03
Bug report filed (pretty much copied this page) [https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/408306](https://bugs.launchpad.net/ubuntu/+source/dhcp3/+bug/408306)

---

### Post by SilvaRizla on 2009-08-03
OK, I think I am starting to get somewhere now, I have installed pump (an alternative dchpclient) and can now get an IP from my router.  However the connection drops off and I have to sudo ifdown wlan0 and ifup again to get it back to the router, only for it to drop off again.

I also can't access web pages (not even router page) but I can dig @192.168.0.1 ubuntu.com (yahoo.com etc)


Can anyone help?

---

### Post by alfal on 2009-08-14
try this

Code:
     sudo apt-get install linux-backports-modules-jaunty

---

