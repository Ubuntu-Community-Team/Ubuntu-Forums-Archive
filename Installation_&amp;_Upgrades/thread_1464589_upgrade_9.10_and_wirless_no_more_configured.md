---
title: "upgrade 9.10 and wirless no more configured"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by MasMas on 2010-04-28
Upgrade to 9.10 and wireless no more function... (i have a rtl8187, use ndiswrapper with win98 drivers) 
Drivers seems ok, iwconfig says me:
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

even if in network/interfaces there is the configuration (even the essid) and in 9.04 it worked...

Network manager disabled, all manually configured.

If I try to set the essid manually with:
iwconfig wlan0 essid QUAGLIOTES
it remains unconfigured...

What can be? What is changed since 9.04 in wireless configuration?

---

### Post by MasMas on 2010-04-30
Does anyone has a 9.10 installed on a asus p5b deluxe?

---

### Post by MasMas on 2010-05-05
Even it seems no one is interested, I figured out what happened:

1. I have disabled the ipv6 support that was disabled in the previous version in the file aliases, but now it's no more there (and the installation deleted without sayng nothing).

2. I have removed wpa_supplicant because it does not function with my card/driver, I've tryed to configure it but I've found a thousand guides saying all different things (and no one single complete manual), and I have an open network that filter machines by mac address.

So I have resolved.

---

