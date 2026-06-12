---
title: "Ubuntu Server 11.10-  No WiFi after apt-get install ubuntu-desktop"
date: 2012-12-10
forum: Installation &amp; Upgrades
---

### Post by machouinard on 2012-12-10
I had 11.10 server running great.  I'm in the middle of moving and my other machines are at the new house so I ran apt-get install ubuntu-desktop in the hopes of being able to get some work done that came up tonight. After installing desktop, I'm unable to connect to wifi (I'd need to move the machine several rooms and one floor away to connect directly to the router).

I was getting a *Not Managed* error but after setting *managed=true* in NetworkManager.conf I'm now getting *Wireless Networks Device not ready*. It's been a while since I set up this server (11.10) and that was my first experience with a linux server.  Needless to say, I'm a bit lost.

I could really use a shove in the right direction.

Thanks much,
Mark

EDIT: *device not ready* is the only message.  There is nothing about firmware missing, as I've read elsewhere.

EDIT 2:  
I've  moved closer to the router and eth0 is working just fine.
For what it's worth, here is what I get from *iwscan wlan0 scan*.  I used to get a list of all the wireless routers in the neighborhood so I don't know if this actually sees the router or if this is just stored info...

wlan0     Scan completed :
          Cell 01 - Address: 00:1E:58:23:F6:F3
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=70/70  Signal level=-30 dBm  
                    Encryption key:on
                    ESSID:"MAC"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001ee4ceb298
                    Extra: Last beacon: 46596ms ago
                    IE: Unknown: 00034D5243
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030105
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1605071B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340507030000000F000000000000000000000000000000
                    IE: Unknown: DD7F0050F204104A0001101044000102103B00010310470010F4B5C4059C2C354A809DD7F0BE4739B21021000E442D4C696E6B2053797374656D73102300074449522D363535102400024133104200046E6F6E651054000800060050F204000110110017587472656D65204E204749474142495420526F7574657210080002008C

---

### Post by machouinard on 2012-12-10
So I swapped the wireless nic with another of the same model and all is working.  Guess the thing somehow went bad after I installed ubuntu-desktop.  Strange.

---

### Post by Bucky Ball on 2012-12-10
Welcome to the forums.

Probably dying already and coincidental. These things seem to happen that way. Can you try the 'dead' one in another machine to verify, perhaps?

Please mark thread as 'Solved' from 'Thread Tools' when you are satisfied it is. ;)


PS: You realise that ubuntu-desktop drags in EVERYTHING a regular Ubuntu install would have? All apps and desktop environment (which in your case is probably Unity)? Not ideal for a server. You now have Ubuntu Desktop Edition setup as a server. 

The usual procedure is to just install the desktop environment if you want a desktop to work with, xfce4 or lxde good, light choices. Just thought I'd mention ... ;)

PPS: Servers usually use the long term support releases for stability. 11.10 will be unsupported April 2013. 12.04 LTS is supported for five years, until April 2017.

---

