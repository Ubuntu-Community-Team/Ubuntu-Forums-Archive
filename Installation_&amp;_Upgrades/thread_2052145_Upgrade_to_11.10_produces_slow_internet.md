---
title: "Upgrade to 11.10 produces slow internet"
date: 2012-09-02
forum: Installation &amp; Upgrades
---

### Post by gtdcubo on 2012-09-02
Have recently upgraded to from 10.10 11.10 via 11.04 to keep up to date. The 10.10 => 11.04 & 11.04 => 11.10 were done on consecutive days because the first upgrade left many things not working. The problem in this post concerns 11.10.

The symptoms are that the internet connection is noticeably laggy and this applies to Chromium, Chrome and Firefox browsers equally. However the apt-get downloads in the Terminal appear not to be affected by this issue. That is to say, apt-get appears speedy. 

We are using the gnome desktop as frankly the other one which is default for 11.10 is inadequate and counter-intuitive for our needs. However, I have tested whether the introduction of this extra presentation layer is responsible for the lagging internet. However it is not. The internet goes equally slow with the new interface (the one with the icons lined up along the LH side of the desktop where everything that used to be available with gnome is now obfuscated and well hidden). 

I actually have had 11.10 installed on my laptop for a year, and with the same home wifi there are not slowness problems. Therefore we will assume that this is an issue limited to my desktop PC whose spec we can see here

```
paul@VLC-GF7050VT-M:~$ lspci
00:00.0 Host bridge: nVidia Corporation Device 07c3 (rev a2)
00:00.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a2)
00:01.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.1 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.2 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.3 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.4 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.5 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:01.6 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:02.0 RAM memory: nVidia Corporation nForce 630i memory controller (rev a1)
00:03.0 ISA bridge: nVidia Corporation MCP73 LPC Bridge (rev a2)
00:03.1 SMBus: nVidia Corporation MCP73 SMBus (rev a1)
00:03.2 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:03.4 RAM memory: nVidia Corporation MCP73 Memory Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation GeForce 7100/nForce 630i USB (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP73 [nForce 630i] USB 2.0 Controller (EHCI) (rev a1)
00:08.0 IDE interface: nVidia Corporation MCP73 IDE (rev a1)
00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0b.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0c.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0d.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP73 IDE (rev a2)
00:0f.0 Ethernet controller: nVidia Corporation MCP73 Ethernet (rev a2)
01:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
02:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]
paul@VLC-GF7050VT-M:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 13b1:000d Linksys WUSB54G v4 802.11g Adapter [Ralink RT2500USB]
Bus 001 Device 005: ID 0bda:0111 Realtek Semiconductor Corp. Card Reader
Bus 001 Device 006: ID 1d0d:0214  
Bus 002 Device 002: ID 046d:0928 Logitech, Inc. QuickCam Express
Bus 002 Device 003: ID 15d9:0a33 Trust International B.V. Optical Mouse
paul@VLC-GF7050VT-M:~$ dmidecode^C
paul@VLC-GF7050VT-M:~$ 

```

The internet related attributes are here  

```
paul@VLC-GF7050VT-M:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:90:63:9f:ac  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1896 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1896 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:110897 (110.8 KB)  TX bytes:110897 (110.8 KB)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          inet addr:192.168.79.1  Bcast:192.168.79.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          inet addr:192.168.26.1  Bcast:192.168.26.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:374 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:96:81:20  
          inet addr:192.168.1.33  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1460  Metric:1
          RX packets:30638 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32203 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:22391872 (22.3 MB)  TX bytes:6860834 (6.8 MB)
```

We are aware that this is not an unusual problem and can therefore certify that before opening this post all of the following solutions were implemented, none of which produced any improvement in the speed of the internet connection.

In this list I will cite the web site then quote the operation carried out.

[http://askubuntu.com/questions/73523/wireless-internet-connection-so-slow-after-upgrade-to-11-10](http://askubuntu.com/questions/73523/wireless-internet-connection-so-slow-after-upgrade-to-11-10)

[INDENT]```
gksu gedit /etc/modprobe.d/options.conf
```[/INDENT]

[INDENT]and add the line[/INDENT]

[INDENT]```
options iwlagn 11n_disable=1
```[/INDENT]

[http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/](http://www.unixmen.com/resolve-slow-connexion-when-using-wifi-in-ubuntu-1104-natty-narwhal/)

[INDENT]```
sudo -s gksu gedit /etc/modprobe.d/ath9k.conf
```[/INDENT]

[INDENT]at the end of the file add this:[/INDENT]

[INDENT]```
options ath9k nohwcrypt=1
```[/INDENT]

as well as


[INDENT]```
gksudo gedit /etc/modprobe.d/iwlagn-disable11n.conf
```[/INDENT]

[INDENT]and add this line to the file:[/INDENT]

[INDENT]```
options iwlagn 11n_disable=1
```[/INDENT]


In fact I have tried more solutions than just these, but they are too numerous the mention. For example I have IP6 disabled and have various non auto settings in the ip4 connection.

The fact of the matter is I have changed more things than I care to remember, none of which have improved internet speeds. 

I am upset at having updated from my beloved Ubuntu 10.10 which had no real problems other than a popup informing me that it was no longer supported.

If anyone can shed light in this I will be grateful.

Thanks for your attention

---

### Post by gtdcubo on 2012-09-04
Can I assume that the fact I have had no replies means one of the following?
1. That I appear to have done everything right and therefore it is inexplicable why I have slow dial up speeds with my internet that was fast when I was using 10.10, and therefore no one can offer any further suggestions.
or
2. That no one can be bothered to reply.

---

### Post by gtdcubo on 2012-09-08
Oops this problem of this upgrade is not attributable to 11.10 upgrade as such, but the following. There was slowness at first during which I deleted and recreated the network connection. But in doing so I forgot that I use open DNS and not the native DNS servers of my ISP. In resetting up the connection I neglected to use Open DNS, and therefore the solution to the slowness - which was most probably solved by one of my interventions at the terminal prompt - remained obfuscated. As soon as I edited the connection to use Open DNS I found that network response times returned to satisfactory levels. 

Here is a the article that reminded me about Open DNS

[http://askubuntu.com/questions/66989/ubuntu-11-10-network-speed](http://askubuntu.com/questions/66989/ubuntu-11-10-network-speed) 

Go down to the reply by José C Alavez 26/10/11 at 01:27

---

