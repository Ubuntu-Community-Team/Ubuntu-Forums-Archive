---
title: "wireless problem in ubuntu 10.10"
date: 2011-03-23
forum: Installation &amp; Upgrades
---

### Post by mirinamulhaq on 2011-03-23
[SIZE=4]hello
i recently installed ubuntu 10.10 on my Vaio laptop(VGN-NW_23 NE), however i have some problem with my wireless/wifi connection.
as i enter the key for my WPA & WPA2 connection ,the wireless applet keeps on trying to connect to the wireless but fails everytime and keeps on asking for the key again and again.
my Lan is working fine and i had not this problem n Ubuntu 9.10, which i just removed in favour of 10.10 !!!!
kindly help.[/SIZE]

---

### Post by Mylastconfusion on 2011-03-23
I have exactly the same problem but on a dell dimension 3100. Running the wireless with a belkin  f5d8053 N usb adaptor. I have tried to follow this: 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)
but when I try to run the belkin driver with "wine" I get a message saying my .exe file is not executable and yet I cannot change the permissions to make it executable when i go to its properties... I'm stuck and cannot understand other ways of resolving this problem... Please help!

Is this an Ubuntu 10.10 problem or is it the driver?

---

### Post by mirinamulhaq on 2011-03-23
> **Mylastconfusion said:**
> I have exactly the same problem but on a dell dimension 3100. Running the wireless with a belkin  f5d8053 N usb adaptor. I have tried to follow this: 
[https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053](https://help.ubuntu.com/community/WifiDocs/Device/Belkin%20F5D8053)
but when I try to run the belkin driver with "wine" I get a message saying my .exe file is not executable and yet I cannot change the permissions to make it executable when i go to its properties... I'm stuck and cannot understand other ways of resolving this problem... Please help!

Is this an Ubuntu 10.10 problem or is it the driver?

it seems that it is not a good idea to release the upgrade in just six months.canonical should better take time to test the release thouroughly and then release.
while i was googling for this problem i came to know that it is very common problem with ubuntu 10.10.
i even had some problems with mouse (continuousfreezing), however i managed to solve that.but the wireless problem is terrible

---

### Post by mirinamulhaq on 2011-03-24
[SIZE=4]> **mirinamulhaq said:**
> it seems that it is not a good idea to release the upgrade in just six months.canonical should better take time to test the release thouroughly and then release.
while i was googling for this problem i came to know that it is very common problem with ubuntu 10.10.
i even had some problems with mouse (continuousfreezing), however i managed to solve that.but the wireless problem is terrible

i am including the results of some commands below.

*-network               
       description: Ethernet interface
       product: 88E8057 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 10
       serial: 00:24:be:83:50:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A ip=172.16.1.96 latency=0 multicast=yes
       resources: irq:43 memory:d3920000-d3923fff ioport:d000(size=256) memory:d3900000-d391ffff
  *-network
       description: Wireless interface
       product: AR928X Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 01
       serial: 2c:81:58:e7:27:a6
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=2.6.35-28-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:d2500000-d250ffff



root@inam:~# lsmod | grep ath
ath9k                 101858  0 
ath9k_common            6874  1 ath9k
ath9k_hw              314731  2 ath9k,ath9k_common
ath                    10413  2 ath9k,ath9k_hw
mac80211              267099  2 ath9k,ath9k_common
cfg80211              170485  4 ath9k,ath9k_common,ath,mac80211
led_class               3393  2 ath9k,sdhci




root@inam:~# rfkill list
0: sony-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: sony-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no



root@inam:~# sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Livebox-ba80"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:19:70:50:BF:1D   
          Bit Rate=39 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


root@inam:~# ping -c 4 127.0.0.1
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data.
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.037 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.030 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.031 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.037 ms

--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2999ms
rtt min/avg/max/mdev = 0.030/0.033/0.037/0.007 ms
root@inam:~# ping -c 4 [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)


[/SIZE]

---

### Post by mirinamulhaq on 2011-04-09
Hello,
here is a solution to the problem(note my system is 64 bit)
go to synaptic and install following packages
1.linux-backports-modules-compat-wireless-2.6.37-2.6.35-28-generic
2. linux image 2.6.35-28-generic
3. linux backports-modules-net-2.6.35-28-generic
that is it
i think it was a problem with the default kernel loaded on first installtion.
after success ful installation reboot and see things working.

---

