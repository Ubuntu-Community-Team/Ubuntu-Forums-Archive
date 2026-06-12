---
title: "Wifi help needed with MN-720 on Lifebook"
date: 2005-09-10
forum: Installation &amp; Upgrades
---

### Post by spm on 2005-09-10
I love Ubuntu...been running it exclisively on my desktop for 4 months now.

Recently I got a Fujitsu Lifebook 1110P. Perfect for Ubuntu...right!

Everything worked perfectly until sttting up my my PCMCIA Microsoft MN720, The lights dont come on it...and no scanning can be done. 

I use Ndiswrapper with ankh driver.

# ndiswrapper -l
Installed ndis drivers:
mn720-ankh      driver present, hardware present

I even checked the logs: /var/log/kern.log

Sep 10 17:47:53 localhost kernel: PCI: Setting latency timer of device 0000:01:00.0 to 64
Sep 10 17:47:53 localhost kernel: ndiswrapper: using irq 9
Sep 10 17:47:54 localhost kernel: wlan0: ndiswrapper ethernet device 00:0d:3a:72:8e:97 using driver mn720-ankh
Sep 10 17:47:54 localhost kernel: wlan0: encryption modes supported: WEP

And iwconfig

 # iwconfig wlan0
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:16 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I cant set its ESSID id either...Here is the  conf from /etc/ndiswrapper

/etc/ndiswrapper/mn720-ankh # cat 14E4:4325.conf
NdisVersion|0x50001
Environment|1
BusType|5
mac_address|XX:XX:XX:XX:XX:XX
ndis_version|Microsoft,06/13/2003, 3.20.23.0

antdiv|3
BTCoexist|1
Channel|11
EnableLEAP|1
frag|2346
IBSSGMode|2
Interference_Mode|-1
LegacyMode|0
NetworkAddress|
PLCPHeader|0
PowerSaveMode|0
RadioState|1
Rate|0
rts|2347


Any clues? Dont tell me I have to go back to Windoze for this laptop? Ubunru would be so sweet...

HELP PLEASE THANKS!

spm

---

### Post by kosmic on 2005-09-11
You can try this link -> [http://www.linuxquestions.org/hcl/showproduct.php?product=2100&sort=8&cat=myprod&page=1]("http://www.linuxquestions.org/hcl/showproduct.php?product=2100&sort=8&cat=myprod&page=1")

It is for Suse and rpm packages but with some tweaking you can apply that to ubuntu.

Hope it helps

---

### Post by spm on 2005-09-13
Thanks! Well I got the lites to turn on...

I had to set RadioState to 0 not 1 in the conf file under ndiswrapper.

Now trying to get connection to my hub, somehow cant seem to get an ipaddress.

---

### Post by spm on 2005-09-15
I got it to work! Yeah...

Posting this so if anyone needs to have this work.

I got it to work by downloading manually ndiswrapper 1.1

There's a HOW-TO for it here somewhere!

---

