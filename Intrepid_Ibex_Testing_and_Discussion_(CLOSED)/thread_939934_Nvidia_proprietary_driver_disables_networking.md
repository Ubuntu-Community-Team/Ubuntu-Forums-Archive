---
title: "Nvidia proprietary driver disables networking"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Kakurady on 2008-10-06
If I enable Nvidia proprietary driver, I won't be able to connect to the network.
Just updated from Hardy yesterday and it works fine. Only stopped working after I did some updates today.

Dell Inspiron 1520.
There was one possibly related bug, but it was for Hardy Beta.

---

### Post by Jonie on 2008-10-06
It seems that last update to Network Manager in Gnome borked it. However, if I run dhclient eth0 manually, network connectivity is restored. NM does not list wireless networks anymore, either.

Edit: I found that after update the interface state has been set to unmanaged in /etc/NetworkManager/mn-system-settings.conf

---

### Post by tj111 on 2008-10-06
> **Jonie said:**
> 
Edit: I found that after update the interface state has been set to unmanaged in /etc/NetworkManager/mn-system-settings.conf

Same problem here.  Actually immedaitely after upgrade to 8.10 today eth0 was disabled as well in /etc/network/interfaces.  After enabling that and fixing the nvidia drivers, booted up to see NM saying no connections available (even though I'm posting this from that computer).  Saw your post, set managed=true in that file, and still no luck.  Any advice would rock.

Edit:  Here's the terminal output from NM.
> 
[B]tj@tj ~
$[/B] sudo /etc/init.d/NetworkManager stop
Stopping Network connection manager daemon: NetworkManager.
[B]
tj@tj ~
$[/B] sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  eth0: driver is 'e1000e'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_13_72_28_c5_cf
NetworkManager: <info>  (eth0): now unmanaged
NetworkManager: <info>  (eth0): carrier now ON (device state 1)

And here's my nm-system-settings.conf
> 
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true

Hope I didn't fry my network card.

---

### Post by Kakurady on 2008-10-07
Just restarting NetworkManager worked for me. Weird! Anyone has any idea what's happening here?

Hmm... e1000e. Then it could be a different problem altogether.

```
nekoyasha@Nekokoneko:~$ sudo NetworkManager --no-daemon
NetworkManager: <info>  starting...
NetworkManager: <info>  Found radio killswitch /org/freedesktop/Hal/devices/dell_wlan_switch
NetworkManager: <info>  eth0: driver is 'NULL(info.linux.driver)'.
NetworkManager: <info>  Found new Ethernet device 'eth0'.
NetworkManager: <info>  (eth0): exported as /org/freedesktop/Hal/devices/net_00_1c_23_92_86_57
NetworkManager: <info>  wlan0: driver is 'iwl3945'.
NetworkManager: <info>  wlan0: driver supports SSID scans (scan_capa 0x01).
NetworkManager: <info>  Found new 802.11 WiFi device 'wlan0'.
NetworkManager: <info>  (wlan0): exported as /org/freedesktop/Hal/devices/net_00_1b_77_c2_dc_a8
NetworkManager: <**WARN**>  killswitch_getpower_reply(): Error getting killswitch power: dellWirelessCtl (/usr/bin/dellWirelessCtl) not available or executable.
NetworkManager: <info>  (eth0): device state change: 1 -> 2
NetworkManager: <info>  (eth0): bringing up device.
NetworkManager: <info>  (eth0): preparing device.
NetworkManager: <info>  (eth0): deactivating device.
NetworkManager: <info>  (wlan0): device state change: 1 -> 2
NetworkManager: <info>  (wlan0): bringing up device.
NetworkManager: <info>  (wlan0): preparing device.
NetworkManager: <info>  (wlan0): deactivating device.
NetworkManager: <info>  (wlan0): device state change: 2 -> 3
NetworkManager: <info>  (wlan0): supplicant interface state change: 1 -> 2.
NetworkManager: <info>  (eth0): carrier now ON (device state 2)
NetworkManager: <info>  (eth0): device state change: 2 -> 3
NetworkManager: <info>  Activation (eth0) starting connection 'Auto eth0'
NetworkManager: <info>  (eth0): device state change: 3 -> 4
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  (eth0): device state change: 4 -> 5
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) successful.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
NetworkManager: <info>  Activation (eth0) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) started...
NetworkManager: <info>  (eth0): device state change: 5 -> 7
NetworkManager: <info>  Activation (eth0) Beginning DHCP transaction.
NetworkManager: <info>  dhclient started with pid 8353
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

NetworkManager: <info>  Activation (eth0) Stage 3 of 5 (IP Configure Start) complete.
wmaster0: unknown hardware address type 801
NetworkManager: <info>  DHCP: device eth0 state changed (null) -> preinit
wmaster0: unknown hardware address type 801
Listening on LPF/eth0/00:1c:23:92:86:57
Sending on   LPF/eth0/00:1c:23:92:86:57
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 173.33.115.65 from 10.22.16.1
DHCPREQUEST of 173.33.115.65 on eth0 to 255.255.255.255 port 67
DHCPACK of 173.33.115.65 from 10.22.16.1
NetworkManager: <info>  DHCP: device eth0 state changed preinit -> bound
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) started...
NetworkManager: <info>    address 173.33.115.65
NetworkManager: <info>    prefix 23 (255.255.254.0)
NetworkManager: <info>    gateway 173.33.114.1
NetworkManager: <info>    hostname 'CPE001c23928657-CM00159a3b7392'
NetworkManager: <info>    nameserver '64.71.255.198'
NetworkManager: <info>    domain name 'phub.net.cable.rogers.com'
NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete.
NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
bound to 173.33.115.65 -- renewal in 249342 seconds.
NetworkManager: <info>  (eth0): device state change: 7 -> 8
NetworkManager: <info>  Policy set (eth0) as default device for routing and DNS.
NetworkManager: <info>  Activation (eth0) successful, device activated.
NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.


```Don't think anything has to do with that killswitch...

Just in case:
```
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "InputDevice"
    Identifier    "Generic Keyboard"
    Driver        "kbd"
    Option        "XkbRules"    "xorg"
    Option        "XkbModel"    "pc105"
    Option        "XkbLayout"    "us"
EndSection

Section "InputDevice"
    Identifier    "Configured Mouse"
    Driver        "vmmouse"
EndSection

Section "InputDevice"
    Identifier    "Synaptics Touchpad"
    Driver        "synaptics"
    Option        "SendCoreEvents"    "true"
    Option        "Device"    "/dev/psaux"
    Option        "Protocol"    "auto-dev"
    Option        "HorizEdgeScroll"    "0"
EndSection

Section "InputDevice"
    Identifier    "stylus"
    Driver        "wacom"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "stylus"
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "eraser"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "eraser"
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "cursor"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "cursor"
    Option        "USB"        "on"
EndSection

Section "InputDevice"
    Driver        "wacom"
    Identifier    "pad"
    Option        "Device"    "/dev/input/wacom"
    Option        "Type"        "pad"
    Option        "USB"        "on"
EndSection

Section "Device"
    Identifier    "Configured Video Device"
    Driver        "nvidia"
    Option        "NoLogo"    "True"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
    HorizSync    28-64
    VertRefresh    43-62
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    Defaultdepth    24
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    screen "Default Screen"
    Inputdevice    "Synaptics Touchpad"
    Inputdevice     "stylus"    "SendCoreEvents"
    Inputdevice     "cursor"    "SendCoreEvents"
    Inputdevice     "eraser"    "SendCoreEvents"
    Inputdevice     "pad"    "SendCoreEvents"
EndSection
Section "Module"
    Load        "glx"
EndSection
```

---

### Post by tj111 on 2008-10-07
So I was sitting around, just browsing the web, when all the sudden I got a pop-up notification from network manager saying eth0 was active and connected at 100mbps or something along those lines.  I ran update-manager probably 4-5 hours ago, weird it decided to start working now.  Heres the output of a dmesg.
```

[ 7205.964162] 0000:04:00.0: eth0: Link is Down
[ 7207.678578] 0000:04:00.0: eth0: Link is Up 100 Mbps Full Duplex, Flow Control: None
[ 7207.678587] 0000:04:00.0: eth0: 10/100 speed: disabling TSO

```

---

### Post by nanog on 2008-10-08
read the post at the top of the page about the e1000e driver and you will understand why your ethernet was disable and then reactivated.

---

### Post by ROWDY!!! on 2008-10-08
Just ran the update then:
got the -6 kernel and new network-manager. From posts thus far it seems that network-manager is causing the problem?
Not sure if this information is any help:
uname -a
Linux slax 2.6.24.5 #1 SMP Wed Apr 23 11:54:07 GMT 2008 i686 AMD Turion(tm) 64 X2 Mobile Technology TL-58 AuthenticAMD GNU/Linux

/*I can't access the internet through ubuntu at the moment */

lsmod | grep eth
forcedeth              49036  0

lspci | grep net
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)

cat /etc/network/interfaces
auto lo
iface lo inet loopback

cat nm-system-settings.conf
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

---

### Post by ROWDY!!! on 2008-10-08
Not sure what changed. Rebooted from SLAX back into Ubuntu and networking is back...

---

### Post by Kakurady on 2008-10-08
Seems that yesterday's update has fixed it. Oh well.
> **nanog said:**
> read the post at the top of the page about the e1000e driver and you will understand why your ethernet was disable and then reactivated.Not using e1000e.

**Edit:** Okay, this is still happening.

---

