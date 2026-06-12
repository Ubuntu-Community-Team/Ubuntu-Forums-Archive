---
title: "unable to connect to secure wifi"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by roboa1983 on 2011-11-20
Hi,
I upgraded to 11.10 and initially I was unable to connect via wi-fi. I followed this [link]("http://www.bigfatostrich.com/2011/10/solved-ubuntu-11-10-wireless-issues/"). After restarting, I can now connect to public wifi networks. However, my local wifi network is password protected (either WPA or WPA2). I have wpasupplicant installed, and I'm not sure what else I could be missing.

Here is the card I am currently using: 
```
lspci -nvn | grep -i net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

Thanks for the help!

---

### Post by fdrake on 2011-11-20
> **roboa1983 said:**
> Hi,
I upgraded to 11.10 and initially I was unable to connect via wi-fi. I followed this [link]("http://www.bigfatostrich.com/2011/10/solved-ubuntu-11-10-wireless-issues/"). After restarting, I can now connect to public wifi networks. However, my local wifi network is password protected (either WPA or WPA2). I have wpasupplicant installed, and I'm not sure what else I could be missing.

Here is the card I am currently using: 
```
lspci -nvn | grep -i net
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express [14e4:1713] (rev 02)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection [8086:4222] (rev 02)

```

Thanks for the help!

can you post 
```

sudo iwlist wlan0 scan | less

```
tell us which one is your essid and make sure u have euther wpa or wpa2 not both. Also old hardware work better with a/b or g mode. n mode sometimes is not very stable.

---

### Post by roboa1983 on 2011-11-21
fdrake, 
Thanks for replying. 
What do you mean by"
> Also old hardware work better with a/b or g mode. n mode sometimes is not very stable.



Here's the output... 
> $ sudo iwlist wlan0 scan
```

wlan0     Scan completed :
          Cell 01 - Address: C0:3F:0E:04:B8:58
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-40 dBm  
                    Encryption key:on
                    ESSID:"LeMarche"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000670e6c0183
                    Extra: Last beacon: 204ms ago
                    IE: Unknown: 00084C654D6172636865
                    IE: Unknown: 010882840B162430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 2F0104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B0001031047001057BF867E57D7A81124BEF7C4C53061CA1021000D4E4554474541522C20496E632E10230009574752363134763130102400095747523631347631301042000538333235381054000800060050F204000110110009574752363134763130100800020084
                    IE: Unknown: DD090010180203F0050000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 11 - Address: 00:03:52:9B:B6:50
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Harvard"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000367afc8418b
                    Extra: Last beacon: 180ms ago
                    IE: Unknown: 000748617276617264
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101840003A4000027A400004243BC0062326600

```

---

### Post by roboa1983 on 2011-12-01
Hi,
It seems my problems were solved when looking at the comments of this thread: [http://ubuntuforums.org/showthread.php?t=1864163](http://ubuntuforums.org/showthread.php?t=1864163) .

I uninstalled network-manager and started using wicd. So far it has been connected and has survived a reboot.

---

