---
title: "Cannot get through to the net with Karmic"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dunbrokin on 2009-10-05
....have no problem with Intrepid (am using the live CD of Karmic Beta)

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:"DLINK"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:FC:86:C6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-26 dBm  Noise level=-91 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions.

---

### Post by ikt on 2009-10-05
> **dunbrokin said:**
> ....have no problem with Intrepid (am using the live CD of Karmic Beta)

ubuntu@ubuntu:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

wmaster0  no wireless extensions. 

wlan0     IEEE 802.11abgn  ESSID:"DLINK"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:3D:FC:86:C6   
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=70/70  Signal level=-26 dBm  Noise level=-91 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions.

if you plug in via ethernet cable,

sudo apt-get install wicd

then unplug ethernet and see if that fixes the issue.

---

