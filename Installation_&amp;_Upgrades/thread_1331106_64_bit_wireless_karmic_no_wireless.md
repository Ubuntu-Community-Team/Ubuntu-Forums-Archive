---
title: "64 bit wireless karmic no wireless"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by dconnors on 2009-11-19
just installed 64 bit karmic  onto my hp dv6000 and it cant seem to find the wireless card..  here are results of iw config. 



 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


any suggestions would be helpful.. thanks 

dale

---

### Post by tommcd on 2009-11-19
Well first tell us what wireless card you have and whether Ubuntu has detected it.
 Run **lspci** in the terminal to list your devices. The wireless should be near the end of the output. Post it here.
Also run **lsmod** to list the drivers that are loaded to see if your wireless driver is being loaded. Post the output of lsmod also.

---

