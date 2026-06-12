---
title: "Ad Hoc networking between ubuntu and windoze vista"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Gonz_91 on 2009-10-08
Hi everyone!

I recently moved to a new town, where I'll be studying for a few years, and since I don't know how long I'll be living in this particular house, I decided to get me some mobile broadband goodness :P
So, I have only one modem, which I plug into my mate's PC (running vista), and create an Ad Hoc network to share the connection with my ipod and my own computer (running wither Ubuntu or Win7).
I can join the network and access the internet while running 7, but on the other hand, Ubuntu seems to be unable to connect to the network. The applet icon just spins until it asks for the password again.

Some specs: I'm running Ubuntu 9.10 beta 1 on a Toshiba Satellite L300. My buddy's sharing the network on a Toshiba Satellite A500, using WEP protection. (I know WEP sucks, but I want access to the internet on my ipod too)

Thanks everyone in advance :D

---

### Post by WindPower on 2009-10-08
Same here but on Kubuntu 9.04 64-bit, without any protection on the network. :(

---

### Post by Gonz_91 on 2009-10-09
It sucks, because it means that I'll only have internet access when I go home, i.e. once a week. :(

---

### Post by ArcaVex on 2009-10-09
If you cannot connect with a network managing tool, like WICD or NetworkManager then try connect from a terminal.

Whats the output of    iwconfig  ?

if wlan0 shows up then try this in terminal


sudo iwconfig wlan0 essid NETWORKSSID   (replace NETWORKSSID with your SSID)
sudo iwconfig wlan0 key WEPKEY               (replace WEPKEY with your WEP key)
sudo dhclient wlan0                                  

if it doesn't connect post output.   (also dhclient could be substituted with dhcpcd if you have that installed instead)

---

### Post by Gonz_91 on 2009-10-09
> **ArcaVex said:**
> If you cannot connect with a network managing tool, like WICD or NetworkManager then try connect from a terminal.

Whats the output of    iwconfig  ?

if wlan0 shows up then try this in terminal


sudo iwconfig wlan0 essid NETWORKSSID   (replace NETWORKSSID with your SSID)
sudo iwconfig wlan0 key WEPKEY               (replace WEPKEY with your WEP key)
sudo dhclient wlan0                                  

if it doesn't connect post output.   (also dhclient could be substituted with dhcpcd if you have that installed instead)

Thanks a lot for your reply!
I am not currently at my 'school home', and am unable to access said computer/modem/network. But I'll go back there on Sunday, try it out, and update.

Thanks a lot once again :D

---

### Post by WindPower on 2009-10-09
> **ArcaVex said:**
> If you cannot connect with a network managing tool, like WICD or NetworkManager then try connect from a terminal.

Whats the output of    iwconfig  ?

if wlan0 shows up then try this in terminal


sudo iwconfig wlan0 essid NETWORKSSID   (replace NETWORKSSID with your SSID)
sudo iwconfig wlan0 key WEPKEY               (replace WEPKEY with your WEP key)
sudo dhclient wlan0                                  

if it doesn't connect post output.   (also dhclient could be substituted with dhcpcd if you have that installed instead)```
$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abgn  ESSID:"<My network name>"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: <My router's MAC address>
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-48 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

pan0      no wireless extensions.
```

I tried running this:
```
sudo ifconfig eth1 down
sudo iwconfig eth1 mode ad-hoc
sudo iwconfig eth1 essid '<the Ad-hoc network's name>'
sudo ifconfig eth1 up
sudo dhclient eth1
```But nothing happens, dhclient just keeps trying to get an IP and fails.

---

