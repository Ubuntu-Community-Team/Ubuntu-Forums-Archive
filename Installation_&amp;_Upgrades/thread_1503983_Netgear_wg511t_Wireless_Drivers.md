---
title: "Netgear wg511t Wireless Drivers"
date: 2010-06-07
forum: Installation &amp; Upgrades
---

### Post by DrPinsLove on 2010-06-07
Hi everyone, 
I'm pretty new to lubuntu and linux. 

I need to get my wireless card up and running on my laptop but apparently the drivers are not native to lubuntu. That or I'm doing something wrong.

So lubuntu is recognizing the wireless device, I get the following statement after I enter iwconfig on terminal.

```
drpinslove@drpinslove-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

``` 

Although it is on managed mode there are no wireless networks recognized. I have the Wicd Network Manager telling me that there's no recognized wireless device attached when terminal tells me otherwise.

Thanks for your help ahead of time.

---

### Post by dino99 on 2010-06-07
[http://ohioloco.ubuntuforums.org/showthread.php?t=1017721](http://ohioloco.ubuntuforums.org/showthread.php?t=1017721)

[http://www.google.com/search?as_q=wg511t%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images](http://www.google.com/search?as_q=wg511t%2Blucid&hl=fr&num=10&btnG=Recherche+Google&as_epq=&as_oq=&as_eq=&lr=&cr=&as_ft=i&as_filetype=&as_qdr=y&as_occt=any&as_dt=i&as_sitesearch=&as_rights=&safe=images)

---

### Post by DrPinsLove on 2010-06-07
Thanks for the quick reply!
I'm going to start researching again.

---

### Post by DrPinsLove on 2010-06-07
Almost got it! I know I'm so close! 
I used the madwifi-ng driver installation

```
sudo -i
apt-get update && sudo apt-get upgrade
apt-get install build-essential libssl-dev
apt-get install linux-headers-`uname -r`
apt-get install subversion
svn checkout http://svn.madwifi-project.org/madwifi/trunk/ madwifi-ng
echo "" >> /etc/modprobe.d/blacklist
echo "#Remove To Install MadWIFI Drivers" >> /etc/modprobe.d/blacklist
echo "blacklist ath9k" >> /etc/modprobe.d/blacklist
echo "blacklist ath5k" >> /etc/modprobe.d/blacklist
cd madwifi-ng
make && make install
echo ath_hal >> /etc/modules
echo ath_pci >> /etc/modules
```

Okay so now I have the lights blinking from one side to another. The Wicd still isn't reading surrounding SSIDs and the wireless card looks like it's having a heart attack. But! At least when I type iwconfig I get the following:

```
drpinslove@drpinslove-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.447 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:19 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-96 dBm  Noise level=-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

So the atheros chipset is recognized. However when I enter ifconfig I get the following:

```
drpinslove@drpinslove-laptop:~$ ifconfig
ath0      Link encap:Ethernet  HWaddr 00:1e:2a:64:5c:79  
          inet6 addr: fe80::21e:2aff:fe64:5c79/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth0      Link encap:Ethernet  HWaddr 00:b0:d0:05:74:c5  
          inet addr:192.168.0.8  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2b0:d0ff:fe05:74c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:999 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1026 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:572438 (572.4 KB)  TX bytes:177629 (177.6 KB)
          Interrupt:10 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:276 (276.0 B)  TX bytes:276 (276.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-1E-2A-64-5C-79-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3146 errors:0 dropped:0 overruns:0 frame:479
          TX packets:2600 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:289130 (289.1 KB)  TX bytes:119600 (119.6 KB)
          Interrupt:10 

``` 

So I have no idea what I'm doing wrong... If anyone can continue to help or post a link I will immediately write the solution and this case can finally be closed!

---

### Post by DrPinsLove on 2010-06-07
Bump?

---

### Post by Jose Catre-Vandis on 2010-12-11
I just laid my hands on a wg511t pcmcia card to play with. PLugged it into my Dell 610 laptop running a fairly clean install of Xubuntu Jaunty (9.04). The green light above the A in Netgear cam on after boot. I didn't have connection so clicked on the Network Manager icon. This showed a list of networks, including mine, so I selected it and it started trying to connect.

I then had to go into my router config, to untick the access control (I only use mac address control as opposed to other securities). This then allowed the card to connect.

May be you need to remove security from your router to start off with, then build up from there?

---

