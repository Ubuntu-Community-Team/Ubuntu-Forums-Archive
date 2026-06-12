---
title: "No wired internet"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by Buster95 on 2008-05-01
Installed Hardy on a desktop and a laptop. Both wired to the same router.

Desktop ethernet works OK; laptop doesn't.

Swapped cables:
desktop still works, laptop still doesn't.

Restarted the laptop: Still won't work

Compared network settings:
Both wired connections have roaming disabled and automatic configuration set to DHCP

Below are the two ifconfig outputs - the first is the laptop, the second is the desktop. I can't see what's wrong. Can anyone help me?

Thanks

laptop:~$ ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:90:f5:57:ba:bb  
          inet addr:192.168.0.4  Bcast:192.168.0.255  Mask:255.255.255.0 
          inet6 addr: fe80::290:f5ff:fe57:babb/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:39 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:316 (316.0 B)  TX bytes:8725 (8.5 KB) 
          Interrupt:21 Base address:0xa400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0 
          inet6 addr: ::1/128 Scope:Host 
          UP LOOPBACK RUNNING  MTU:16436  Metric:1 
          RX packets:290 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:290 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:0 
          RX bytes:16180 (15.8 KB)  TX bytes:16180 (15.8 KB) 

wlan0     Link encap:Ethernet  HWaddr 00:15:af:12:7d:b7  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0 
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 

wmaster0  Link encap:UNSPEC  HWaddr 00-15-AF-12-7D-B7-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B) 


HOME-DESKTOP:~$ ifconfig

eth0      Link encap:Ethernet  HWaddr 00:1b:fc:a1:e7:4a  

          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0

          inet6 addr: fe80::21b:fcff:fea1:e74a/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:7760 errors:0 dropped:0 overruns:0 frame:0

          TX packets:6501 errors:0 dropped:0 overruns:0 carrier:2

          collisions:0 txqueuelen:1000 

          RX bytes:5694262 (5.4 MB)  TX bytes:0 (0.0 B)

          Memory:dffc0000-e0000000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:1694 errors:0 dropped:0 overruns:0 frame:0

          TX packets:1694 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:86576 (84.5 KB)  TX bytes:86576 (84.5 KB)

---

### Post by isharra on 2008-05-01
I've not run into this problem myself. I have heard of people having trouble where network manager will want to route to the wireless in preference to the wired nic. As a step in troubleshooting you may want to turn off your wireless and see if it makes a difference.

---

### Post by Aearenda on 2008-05-01
What's the address of the DHCP server? (the router?) It's a little unusual that you have 192.168.0.1 given to the wlan on the laptop - that's a common address used by routers. 

Please post the output from 'route' and the contents of /etc/resolv.conf on both machines.

---

### Post by Steve1961 on 2008-05-01
The no ethernet after installation problem happens a lot when installing Hardy on an eee pc.  The solution, believe it or not, is simply to take the laptop battery out for 30 seconds, put it back in and then reboot.  Worth a try!

---

### Post by Buster95 on 2008-05-01
> **isharra said:**
> I've not run into this problem myself. I have heard of people having trouble where network manager will want to route to the wireless in preference to the wired nic. As a step in troubleshooting you may want to turn off your wireless and see if it makes a difference.

You were right. I turned off the wireless connection and restarted. The wired connection now works.
Thanks

---

### Post by Buster95 on 2008-05-01
> **Aearenda said:**
> What's the address of the DHCP server? (the router?) It's a little unusual that you have 192.168.0.1 given to the wlan on the laptop - that's a common address used by routers. 

Please post the output from 'route' and the contents of /etc/resolv.conf on both machines.

Hello Aerenda,
Although it wasn't my initial question, you may be on to something here. My laptop wireless isn't working either. I was going to get around to that problem next.

Below is the data you asked for. I'm afraid it tells me nothing.

Cheers

laptop:~$ route 
Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
192.168.0.0     *               255.255.255.0   U     0      0        0 eth0 
link-local      *               255.255.0.0     U     1000   0        0 eth0 
default         [www.routerlogin](www.routerlogin) 0.0.0.0         UG    100    0        0 eth0 

Laptop
contents of /etc/resolv.conf
nameserver 192.168.0.1


HOME-DESKTOP:~$ route

Kernel IP routing table

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface

192.168.0.0     *               255.255.255.0   U     0      0        0 eth0

link-local      *               255.255.0.0     U     1000   0        0 eth0

default         [www.routerlogin](www.routerlogin) 0.0.0.0         UG    100    0        0 eth0

DESKTOP
nameserver 192.168.0.1

---

### Post by Aearenda on 2008-05-01
OK, the nameserver entries in /etc/resolv.conf tell you where name resolution is done - in other words, if you type 'www.ubuntu.com' in the address bar of your browser, your PC asks the nameserver PC for the IP address of 'www.ubuntu.com'. It likely doesn't know, but it will pass the query up the chain to your ISP. The address for the nameserver for both desktop and laptop is 192.168.0.1, which tells me that that is the address your router believe it owns.

The route output names the router as 'www.routerlogin' - this should be the name that corresponds to 192.168.0.1 in the router's tables - but just to be sure, 'route -n' will skip the name and print the ip address.

So the question is, why does your laptop wireless lan think it owns 192.168.0.1? This would account for why nothing works when the wireless is turned on. 

Please post the contents of /etc/network/interfaces from the laptop.

Also, please check the DHCP settings on your router. Maybe it isn't smart enough to realise it is allocating it's own IP address to another computer. The range of addresses able to be allocated should start from 192.168.0.2, not 192.168.0.1.

BTW, the route output also tells us where the computer is sending traffic for each subnet. If more than one interface is active, as on the laptop, this tells us which interface is used by default for traffic for the internet. Normally, in roaming mode, Network Manager will select the wired connection (eth0) if present, otherwise the wireless connection (wlan0).

---

### Post by Buster95 on 2008-05-01
> **Aearenda said:**
> OK, the nameserver entries in /etc/resolv.conf tell you where name resolution is done - in other words, if you type 'www.ubuntu.com' in the address bar of your browser, your PC asks the nameserver PC for the IP address of 'www.ubuntu.com'. It likely doesn't know, but it will pass the query up the chain to your ISP. The address for the nameserver for both desktop and laptop is 192.168.0.1, which tells me that that is the address your router believe it owns.

The route output names the router as 'www.routerlogin' - this should be the name that corresponds to 192.168.0.1 in the router's tables - but just to be sure, 'route -n' will skip the name and print the ip address.

So the question is, why does your laptop wireless lan think it owns 192.168.0.1? This would account for why nothing works when the wireless is turned on. 

Please post the contents of /etc/network/interfaces from the laptop.

Also, please check the DHCP settings on your router. Maybe it isn't smart enough to realise it is allocating it's own IP address to another computer. The range of addresses able to be allocated should start from 192.168.0.2, not 192.168.0.1.

BTW, the route output also tells us where the computer is sending traffic for each subnet. If more than one interface is active, as on the laptop, this tells us which interface is used by default for traffic for the internet. Normally, in roaming mode, Network Manager will select the wired connection (eth0) if present, otherwise the wireless connection (wlan0).

Thanks,
copying contents of /etc/network/interfaces below. I have replaced the wireless WEP key with X's.

One other thing that may be relevant here. I used the Hardy upgrade facility for the desktop, but did a fresh Hardy install off a disk for the laptop. That may have changed things a bit.

Cheers

auto lo 
iface lo inet loopback 

iface wlan0 inet static 
address 192.168.0.1 
netmask 255.255.255.0 
wireless-key xxxxxxxxxxx 
wireless-essid NETGEAR 

iface eth0 inet dhcp 

auto eth0

---

### Post by Aearenda on 2008-05-01
Here's your culprit then: The settings for wlan0 force it to use the same IP address as your router. When the wireless is on, it will render the laptop wired interface useless, since the wired interface will then try to route all internet traffic to the wireless interface, which doesn't know what to do with it, and it will probably eventually muck with the desktop's internet access too. Also, the wireless interface has no gateway address, so it can't get anywhere beyond the local subnet.

Is there a good reason to have the wireless interface set static? If not, I would let Network Manager control it, by setting it to roaming mode. 

Otherwise, change that part of /etc/network/interfaces like this:
```
iface wlan0 inet static
address 192.168.0.200
netmask 255.255.255.0
gateway 192.168.0.1
metric 500 
wireless-key xxxxxxxxxxx
wireless-essid NETGEAR 
```
The choice of '200' for the ip address is random, just keep it well away from the DHCP range used by the router. The 'metric' entry will make the computer use the wired interface if possible, since it will appear to be a shorter route.

This should allow everything to work, I think!

---

### Post by Buster95 on 2008-05-01
> **Aearenda said:**
> Here's your culprit then: The settings for wlan0 force it to use the same IP address as your router. When the wireless is on, it will render the laptop wired interface useless, since the wired interface will then try to route all internet traffic to the wireless interface, which doesn't know what to do with it, and it will probably eventually muck with the desktop's internet access too. Also, the wireless interface has no gateway address, so it can't get anywhere beyond the local subnet.

Is there a good reason to have the wireless interface set static? If not, I would let Network Manager control it, by setting it to roaming mode. 

Otherwise, change that part of /etc/network/interfaces like this:
```
iface wlan0 inet static
address 192.168.0.200
netmask 255.255.255.0
gateway 192.168.0.1
metric 500 
wireless-key xxxxxxxxxxx
wireless-essid NETGEAR 
```
The choice of '200' for the ip address is random, just keep it well away from the DHCP range used by the router. The 'metric' entry will make the computer use the wired interface if possible, since it will appear to be a shorter route.

This should allow everything to work, I think!

Thanks,
1 Changed "/etc/network/interfaces" as you suggested. Restarted but no connection. Plugged in the ethernet cable but no automatic reversion to the wired connection. Restarted and the wired connection enabled OK, without having to de-select the wireless as I had done earlier in this thread.

2 Changed wireless to "roaming" via "System/Administration/Network/Network Settings". Removed ethernet cable but no automatic reversion to wireless. Restarted (with the ethernet cable still off), but no wireless connection.

To answer your question "why use the static wireless setting" - I really only intend to use the laptop wirelessly in my home and thought that might produce a more reliable wireless connection than I was able to achieve with previous Ubuntu versions. Previously, wireless connection seemed to be related to the colour of the moon (as in "once in a blue moon"). Looks like Hardy hasn't changed much for me in that regard.

Cheers

---

### Post by Aearenda on 2008-05-02
I would leave it set to roaming mode then.

Assuming you have Network Manager running - in roaming mode you have to click on the network icon on the system tray and tell it to connect to a wireless connection the first time - click on the one with the name NETGEAR. It should then prompt you for the key. 

BTW, after this has all been made to work, it would be a good idea to change the ssid away from NETGEAR in case any neighbours also buy a Netgear router (assuming you're actually in a built up area).
Also, WEP isn't really much of a defence any more - can your router do WPA?

---

### Post by Aearenda on 2008-05-02
And another thought - I should have told you the wired connection should be set to roaming mode too, to get proper automatic switching as the cable is plugged in - otherwise NM will connect to the wireless network regardless, and the effect isharra mentioned then happens.

---

### Post by Buster95 on 2008-05-02
> **Aearenda said:**
> I would leave it set to roaming mode then.

Assuming you have Network Manager running - in roaming mode you have to click on the network icon on the system tray and tell it to connect to a wireless connection the first time - click on the one with the name NETGEAR. It should then prompt you for the key. 

BTW, after this has all been made to work, it would be a good idea to change the ssid away from NETGEAR in case any neighbours also buy a Netgear router (assuming you're actually in a built up area).
Also, WEP isn't really much of a defence any more - can your router do WPA?

Thanks,
I had done the wireless selection steps, but had omitted to mention it. The wireless applet generates the little bars icon and shows 90% - 98% signal (the laptop is about half a metre away from the wireless router).
However, it still can't find a web site and every minute or so the wireless passphrase box pops up again requesting the passkey.

I just logged onto my router and switched off the WEP. The router is now freely accessible for the moment.

That's not such a problem where I live. My "cheap-as-chips" laptop, my sons top end Mac and my daughters mid range Toshiba (running WXP) can see no other networks in the area, so I'm probably safe for a while.

The wireless applet still shows 95% signal and indicates that the laptop is connected to it. Tried 3 times and got a connection to Google after approximately 2 minutes on one of the 3 occasions. The 4th try is still grinding away after 5 minutes.

Go figure that one!

---

### Post by Aearenda on 2008-05-02
This sounds more like driver problems now - what sort of wireless interface is it? Are you using ndiswrapper or a native driver (the latter unless you've deliberately changed it)?
```
lspci
``` will tell you the hardware on the PCI bus.

What speed is it going at?
```
iwconfig
```
will tell us that and other things.

Network manager logs all its actions in /var/log/daemon.log...
```
grep NetworkManager /var/log/daemon.log
```
should tell us whether it thinks it has a good connection, amongst a load of other stuff.

---

### Post by Buster95 on 2008-05-02
> **Aearenda said:**
> This sounds more like driver problems now - what sort of wireless interface is it? Are you using ndiswrapper or a native driver (the latter unless you've deliberately changed it)?
```
lspci
``` will tell you the hardware on the PCI bus.

What speed is it going at?
```
iwconfig
```
will tell us that and other things.

Network manager logs all its actions in /var/log/daemon.log...
```
grep NetworkManager /var/log/daemon.log
```
should tell us whether it thinks it has a good connection, amongst a load of other stuff.

The wireless interface is a Realtek RTL8187 internal usb system, using whatever driver comes with Hardy. In earler releases, I have tried ndiswrapper and alternative drivers from Realtek as well as hacked versions from various geniuses on this site. None have essentially changed the unreliability of wireless connection:
laptop:~$ lsusb 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 0bda:8187 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 0402:5602 ALi Corp. Video Camera Controller 
Bus 001 Device 001: ID 0000:0000   
Bus 001 Device 001: ID 0000:0000  

As stated earlier in the thread, the wireless is in roaming mode and the router is within spitting distance:

laptop:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:18:4D:C0:B8:D6   
          Bit Rate=1 Mb/s   Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality=57/64  Signal level=61/65  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

The following epistle is the /var/log/daemon.log. I didn't know how to shorten it.

EAR' 
May  2 14:24:28 dexter-laptop NetworkManager: <debug> [1209702268.957488] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'NETGEAR' 
May  2 14:24:28 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:24:40 dexter-laptop NetworkManager: <info>  Supplicant state changed: 1 
May  2 14:24:40 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'NETGEAR'. 
May  2 14:24:40 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  2 14:24:40 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
May  2 14:24:41 dexter-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
May  2 14:24:41 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May  2 14:24:41 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May  2 14:24:42 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May  2 14:24:45 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:25:08 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
May  2 14:25:08 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  2 14:25:08 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May  2 14:25:09 dexter-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May  2 14:25:09 dexter-laptop NetworkManager: <info>    address 192.168.0.6 
May  2 14:25:09 dexter-laptop NetworkManager: <info>    netmask 255.255.255.0 
May  2 14:25:09 dexter-laptop NetworkManager: <info>    broadcast 192.168.0.255 
May  2 14:25:09 dexter-laptop NetworkManager: <info>    gateway 192.168.0.1 
May  2 14:25:09 dexter-laptop NetworkManager: <info>    nameserver 192.168.0.1 
May  2 14:25:09 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  2 14:25:09 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May  2 14:25:09 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May  2 14:25:10 dexter-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
May  2 14:25:10 dexter-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  2 14:25:10 dexter-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May  2 14:25:10 dexter-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May  2 14:25:10 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May  2 14:25:10 dexter-laptop NetworkManager: <debug> [1209702310.574713] nm_dbus_signal_filter(): NetworkManagerInfo triggered update of wireless network 'NETGEAR' 
May  2 14:30:01 dexter-laptop NetworkManager: <info>  Supplicant state changed: 0 
May  2 14:37:51 dexter-laptop NetworkManager: <debug> [1209703071.135157] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'NETGEAR' 
May  2 14:37:51 dexter-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / NETGEAR 
May  2 14:37:51 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) started... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  2 14:37:52 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'NETGEAR' is unencrypted, no key needed. 
May  2 14:37:53 dexter-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May  2 14:37:53 dexter-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May  2 14:37:53 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: response was '0' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e455447454152' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:54 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  2 14:37:55 dexter-laptop NetworkManager: <debug> [1209703075.836466] nm_device_802_11_wireless_get_activation_ap(): Forcing AP 'NETGEAR' 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  User Switch: /org/freedesktop/NetworkManager/Devices/wlan0 / NETGEAR 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Activation (wlan0): cancelling... 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Activation (wlan0) cancellation handler scheduled... 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Activation (wlan0): waiting for device to cancel activation. 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Activation (wlan0) cancellation handled. 
May  2 14:37:55 dexter-laptop NetworkManager: <info>  Activation (wlan0): cancelled. 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) started... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  2 14:37:56 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'NETGEAR' is unencrypted, no key needed. 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was '0' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e455447454152' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:37:58 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  2 14:38:03 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:39:00 dexter-laptop NetworkManager: <info>  starting... 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rtl8187'. 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May  2 14:39:10 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 14:39:10 dexter-laptop NetworkManager: <debug> [1209703150.452282] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7530A'). 
May  2 14:39:10 dexter-laptop NetworkManager: <debug> [1209703150.453373] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Will activate connection 'wlan0/NETGEAR'. 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) started... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  2 14:39:38 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'NETGEAR' is unencrypted, no key needed. 
May  2 14:39:39 dexter-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=1) 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  retry to connect to global supplicant socket (try=2) 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was '0' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e455447454152' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:39:40 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  2 14:39:48 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:40:01 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:40:09 dexter-laptop NetworkManager: <info>  Supplicant state changed: 1 
May  2 14:40:09 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to access point 'NETGEAR'. 
May  2 14:40:09 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled. 
May  2 14:40:09 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started... 
May  2 14:40:10 dexter-laptop NetworkManager: <info>  Activation (wlan0) Beginning DHCP transaction. 
May  2 14:40:10 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete. 
May  2 14:40:10 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 12 (successfully started) for interface wlan0 
May  2 14:40:11 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 1 (starting) for interface wlan0 
May  2 14:40:14 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 2 (bound) for interface wlan0 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) scheduled... 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) started... 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon: 
May  2 14:40:15 dexter-laptop NetworkManager: <info>    address 192.168.0.6 
May  2 14:40:15 dexter-laptop NetworkManager: <info>    netmask 255.255.255.0 
May  2 14:40:15 dexter-laptop NetworkManager: <info>    broadcast 192.168.0.255 
May  2 14:40:15 dexter-laptop NetworkManager: <info>    gateway 192.168.0.1 
May  2 14:40:15 dexter-laptop NetworkManager: <info>    nameserver 192.168.0.1 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled... 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP Configure Get) complete. 
May  2 14:40:15 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started... 
May  2 14:40:16 dexter-laptop NetworkManager: <info>  Clearing nscd hosts cache. 
May  2 14:40:16 dexter-laptop NetworkManager: <WARN>  nm_spawn_process(): nm_spawn_process('/usr/sbin/nscd -i hosts'): could not spawn process. (Failed to execute child process "/usr/sbin/nscd" (No such file or directory))  
May  2 14:40:16 dexter-laptop NetworkManager: <info>  Activation (wlan0) successful, device activated. 
May  2 14:40:16 dexter-laptop NetworkManager: <info>  Activation (wlan0) Finish handler scheduled. 
May  2 14:40:16 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete. 
May  2 14:40:28 dexter-laptop NetworkManager: <info>  Supplicant state changed: 0 
May  2 14:41:13 dexter-laptop NetworkManager: <info>  Supplicant state changed: 1 
May  2 14:41:58 dexter-laptop NetworkManager: <info>  Supplicant state changed: 0 
May  2 14:42:18 dexter-laptop NetworkManager: <info>  wlan0: link timed out. 
May  2 14:42:18 dexter-laptop NetworkManager: <info>  SWITCH: found better connection 'wlan0/NETGEAR' than current connection 'wlan0/NETGEAR'.  same_ssid=1, have_link=0 
May  2 14:42:18 dexter-laptop NetworkManager: <info>  Will activate connection 'wlan0/NETGEAR'. 
May  2 14:42:18 dexter-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May  2 14:42:18 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) started... 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'NETGEAR' is unencrypted, no key needed. 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 11 (unknown) for interface wlan0 
May  2 14:42:19 dexter-laptop NetworkManager: <info>  DHCP daemon state is now 14 (normal exit) for interface wlan0 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'INTERFACE_ADD wlan0^I^Iwext^I/var/run/wpa_supplicant0^I' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'AP_SCAN 1' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'ADD_NETWORK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was '0' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 ssid 4e455447454152' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'SET_NETWORK 0 key_mgmt NONE' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: sending command 'ENABLE_NETWORK 0' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  SUP: response was 'OK' 
May  2 14:42:21 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  2 14:42:24 dexter-laptop NetworkManager: <info>  Old device 'wlan0' activating, won't change. 
May  2 14:43:21 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): association took too long (>60s), failing activation. 
May  2 14:43:21 dexter-laptop NetworkManager: <info>  Activation (wlan0) failure scheduled... 
May  2 14:43:21 dexter-laptop NetworkManager: <info>  Activation (wlan0) failed for access point (NETGEAR) 
May  2 14:43:21 dexter-laptop NetworkManager: <info>  Activation (wlan0) failed. 
May  2 14:43:21 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 16:15:29 dexter-laptop NetworkManager: <debug> [1209708929.544832] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623'). 
May  2 16:15:30 dexter-laptop NetworkManager: <debug> [1209708930.290046] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0'). 
May  2 16:15:35 dexter-laptop NetworkManager: <debug> [1209708935.829854] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host'). 
May  2 16:15:35 dexter-laptop NetworkManager: <debug> [1209708935.831701] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0'). 
May  2 16:15:35 dexter-laptop NetworkManager: <debug> [1209708935.833482] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  2 16:15:36 dexter-laptop NetworkManager: <debug> [1209708936.109641] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Flash_Drive_SM_USB20_AA04012700042623_0_0'). 
May  2 16:15:36 dexter-laptop NetworkManager: <debug> [1209708936.157814] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D439_4564'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709108.566512] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709108.569081] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Flash_Drive_SM_USB20_AA04012700042623_0_0'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709108.571373] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709108.571478] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709109.019698] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D439_4564'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709109.021927] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0'). 
May  2 16:18:29 dexter-laptop NetworkManager: <debug> [1209709109.025560] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623'). 
May  2 16:21:32 dexter-laptop NetworkManager: <debug> [1209709292.290374] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623'). 
May  2 16:21:32 dexter-laptop NetworkManager: <debug> [1209709292.358308] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0'). 
May  2 16:21:37 dexter-laptop NetworkManager: <debug> [1209709297.339104] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host'). 
May  2 16:21:37 dexter-laptop NetworkManager: <debug> [1209709297.339825] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0'). 
May  2 16:21:37 dexter-laptop NetworkManager: <debug> [1209709297.340765] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  2 16:21:37 dexter-laptop NetworkManager: <debug> [1209709297.422292] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Flash_Drive_SM_USB20_AA04012700042623_0_0'). 
May  2 16:21:37 dexter-laptop NetworkManager: <debug> [1209709297.441633] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D439_4564'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.460548] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.467950] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D439_4564'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.471031] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Flash_Drive_SM_USB20_AA04012700042623_0_0'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.473909] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.474633] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.479587] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0'). 
May  2 16:22:17 dexter-laptop NetworkManager: <debug> [1209709337.484581] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623'). 
May  2 16:33:09 dexter-laptop NetworkManager: <info>  starting... 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  wlan0: Device is fully-supported using driver 'rtl8187'. 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01). 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  nm_device_init(): waiting for device's worker thread to start 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  nm_device_init(): device's worker thread started, continuing. 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  Now managing wireless (802.11) device 'wlan0'. 
May  2 16:33:19 dexter-laptop NetworkManager: <info>  Deactivating device wlan0. 
May  2 16:33:20 dexter-laptop NetworkManager: <debug> [1209710000.004922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_model_DVD_RW_AD_7530A'). 
May  2 16:33:20 dexter-laptop NetworkManager: <debug> [1209710000.004922] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/platform_bluetooth'). 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Updating allowed wireless network lists. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  SWITCH: no current connection, found better connection 'wlan0'. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Will activate connection 'wlan0/NETGEAR'. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Device wlan0 activation scheduled... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) started... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0/wireless): access point 'NETGEAR' is encrypted, but NO valid key exists.  New key needed. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) New wireless user key requested for network 'NETGEAR'. 
May  2 16:38:36 dexter-laptop NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
May  2 16:39:00 dexter-laptop NetworkManager: <debug> [1209710340.838658] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623'). 
May  2 16:39:00 dexter-laptop NetworkManager: <debug> [1209710340.978736] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0'). 
May  2 16:39:06 dexter-laptop NetworkManager: <debug> [1209710346.117596] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host'). 
May  2 16:39:06 dexter-laptop NetworkManager: <debug> [1209710346.121599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0'). 
May  2 16:39:06 dexter-laptop NetworkManager: <debug> [1209710346.121599] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_90c_1000_AA04012700042623_if0_scsi_host_scsi_device_lun0_scsi_generic'). 
May  2 16:39:06 dexter-laptop NetworkManager: <debug> [1209710346.217652] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Flash_Drive_SM_USB20_AA04012700042623_0_0'). 
May  2 16:39:06 dexter-laptop NetworkManager: <debug> [1209710346.261677] nm_hal_device_added(): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_D439_4564'). 
dexter@dexter-laptop:~$

---

### Post by Aearenda on 2008-05-02
Yuk! The NM trace shows it works sometimes, but not for long.

What does ```
sudo lshw -C network
``` show? Amongst other things, it will tell us what driver is actually in use.

Have you tried ```
sudo modprobe mac80211
``` from post 9 in [http://ubuntuforums.org/showthread.php?p=4799658](http://ubuntuforums.org/showthread.php?p=4799658) ?

There's not much more I have to offer with this now - I've never had to get one of these to work. You'll be better off with people who have one to compare.

EDIT: Actually the NM trace shows it is using the rtl8187 driver so skip the lshw.

---

### Post by Aearenda on 2008-05-02
Another suggestion, from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215802](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215802) : ```
sudo iwconfig wlan0 rate 11M
```
This locks the speed. But you are so close to the AP that it should make no difference.

---

### Post by Buster95 on 2008-05-03
> **Aearenda said:**
> Another suggestion, from [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215802](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/215802) : ```
sudo iwconfig wlan0 rate 11M
```
This locks the speed. But you are so close to the AP that it should make no difference.

Tried both of these suggestions. Neither seemed to have an effect. I got 1 connection out of 4 and even that one dropped out shortly after.

Another interesting (and new) phenomenon: I re-established the WEP on the router and now I get the "enter the WEP key" box every few minutes.

It has also been recommended to me to cut my losses and buy something other than the Realtek usb wireless. I've been trying various ideas for many months, so that approach is becoming increasingly attractive.

Any other thoughts?

Cheers

---

### Post by Aearenda on 2008-05-03
The repeated prompts just confirm that the interface is re-associating far too often.

I think the alternate hardware idea is an excellent one at this point!

---

### Post by geekATlarge on 2008-05-04
Buster95, I had network problem (iptables) ... check out [http://ubuntuforums.org/showthread.php?t=781744](http://ubuntuforums.org/showthread.php?t=781744)

---

### Post by Buster95 on 2008-05-04
> **geekATlarge said:**
> Buster95, I had network problem (iptables) ... check out [http://ubuntuforums.org/showthread.php?t=781744](http://ubuntuforums.org/showthread.php?t=781744)

Thanks,
My connection problems are only with wlan0. I have a good and reliable eth0 connection.

However, I will look into the iptable settings as a possible solution.

Cheers

---

