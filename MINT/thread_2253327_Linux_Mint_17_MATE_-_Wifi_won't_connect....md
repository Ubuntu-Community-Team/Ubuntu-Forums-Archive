---
title: "Linux Mint 17 MATE - Wifi won't connect...?"
date: 2014-11-18
forum: MINT
---

### Post by RallyDarkstrike on 2014-11-18
Hi all....just brought my netbook running Mint 17 back from hibernate  and now it won't connect to WiFi. I've tried deleting the saved  connection multiple times, I've tried turning the WiFi on and off with  the laptop's keyboard command, I've restarted the laptop numerous  times.....same issue. It will come up, ask for a password sometimes, I  type it in and hit connect.....a few seconds later, it just goes back to  a "disconnected" state again.

I've restarted the router as well.....still no go.

After  I had brought it out of hibernate the first time when the problem  started, I had run the "nmcli nm" and "sudo service network-manager  restart" commands as sometimes it won't reconnect on return from  hibernate and these commands fix it.....now it just won't plain connect  whatsoever....any ideas or help would be appreciated! [IMG]http://forums.linuxmint.com/images/smilies/icon_sad.gif[/IMG]

Sometimes it goes as far as "Requesting Network address" and then stops and goes back to the "disconnected" state? The internet works fine on Wired, just won't connect on WiFi, on any network...

Thanks for any suggestions! :(

Here are some outputs of a few commands for reference in case they give anybody any clues!


Output of **sudo /usr/lib/linuxmint/mintWifi/mintWifi.py**:
```
-------------------------
* I. scanning WIFI PCI devices...
  -- Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
      ==> PCI ID = 10ec:8199 (rev 22)
-------------------------
* II. querying ndiswrapper...
-------------------------
* III. querying iwconfig...
wlan0     802.11b/g  ESSID:"The_Watchtower"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lo        no wireless extensions.

eth0      no wireless extensions.

-------------------------
* IV. querying ifconfig...
eth0      Link encap:Ethernet  HWaddr 00:24:21:6c:4f:92  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:667 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:52479 (52.4 KB)  TX bytes:52479 (52.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:21:92:4c:93  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:252 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:17448 (17.4 KB)
          Interrupt:17 Memory:f8590000-f8590100 

-------------------------
* V. querying DHCP...
-------------------------
* VI. querying nslookup google.com...
;; connection timed out; no servers could be reached
```

Output of **lsusb**:
```
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

Output of **lspci**:
```
00:00.0 Host bridge: Intel Corporation Mobile 945GSE Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GSE Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 2 (rev 02)
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] (rev 02)
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller (rev 22)
```

Output of **sudo nmcli nm sleep false**:
```
Error in sleep: Already awake
```

---

