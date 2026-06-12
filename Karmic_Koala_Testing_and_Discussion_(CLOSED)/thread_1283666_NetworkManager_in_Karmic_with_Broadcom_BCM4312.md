---
title: "NetworkManager in Karmic with Broadcom BCM4312"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SqRt7744 on 2009-10-05
Hi, I'm setting up a Dell Vostro 1320 for a friend with who needs it for her PhD work. It has a Broadcom wireless card, the BCM4312, and as per the hardware drivers GUI I have installed the STA driver. The broadcom card is assigned eth2, and finds networks when I enter

```

sudo iwlist eth2 scan

```

Now the trouble is that NetworkManager doesn't seem aware of the wireless card. Could this be because of the unusual assignment to eth2 rather than wlan0 or similar? If yes, what can I do about it? Any help is appreciated, I have to return the laptop tomorrow and everything ought to be working!

Thanks for any suggestions!

---

### Post by mikewhatever on 2009-10-05
What do you mean the NM is not aware ...? Doesn't it yell, 'Hey, look, it's BCM4312'?:) What's the problem exactly? Can you see wireless networks by clicking on the NM icon?

Post the outputs of:
ifconfig
cat /etc/network/interfaces

I also think it a bad idea to give beta software to a friend who can't set it up. It would be rather wise to wait about a month after the final release.

---

### Post by SqRt7744 on 2009-10-06
well, NM claims that wireless networks are deactivated, with no option to activate them, can´t scan, connect to, or anything else one would normally associate with being ´aware´ or a wireless card. The interesting point here is that I *can* connect and scan from the command line using iwlist / iwconfig commands.

Re. beta software, I normally would agree, however in this case the version of the R statistical package included with Jaunty is too old for her purposes (BioConductor recommends the version in Karmic), so I decided that we are close enough to release that it would be better to just install karmic rather than manually install the newest versions of the programs she requires.

ifconfig:

```

eth0      Link encap:Ethernet  Hardware Adresse 00:24:e8:bd:ce:12  
          inet Adresse:192.168.1.8  Bcast:192.168.1.255  Maske:255.255.255.0
          inet6-Adresse: fe80::224:e8ff:febd:ce12/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:1040 errors:0 dropped:0 overruns:0 frame:0
          TX packets:900 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:1072680 (1.0 MB)  TX bytes:175379 (175.3 KB)
          Interrupt:31 Basisadresse:0x4000 

eth2      Link encap:Ethernet  Hardware Adresse 00:22:5f:b4:e1:3d  
          inet6-Adresse: fe80::222:5fff:feb4:e13d/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

cat /etc/network/interfaces
```

# The loopback network interface
auto lo
iface lo inet loopback

```

iwconfig:
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```

sudo iwlist eth2 scan
```
eth2      Scan completed :
          Cell 01 - Address: 00:1C:4A:A2:EB:C8
                    ESSID:"XYZ-SL7170"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 02 - Address: 00:19:CB:A0:3A:7A
                    ESSID:"o2DSL"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
          Cell 03 - Address: 00:1B:2F:09:A2:AA
                    ESSID:"christine"
                    Mode:Managed
                    Frequency:2.417 GHz (Channel 2)
                    Quality:5/5  Signal level:-35 dBm  Noise level:-91 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s; 9 Mb/s; 18 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 00:1E:58:BB:9C:BB
                    ESSID:"KD__9269"
                    Mode:Managed
                    Frequency=2.432 GHz (Channel 5)
                    Quality:1/5  Signal level:-87 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD750050F204104A000110103B0001031047001051BA1D81A5B9FA88B1CE001E58BB9CBB104400010110210006442D4C696E6B102300074449522D333030102400074449522D3330301042000830303030303030301054000800060050F2040001101100074449522D33303010080002008E1041000100
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 00:1F:3F:F6:39:63
                    ESSID:"FRITZ!Box Fon WLAN 7113"
                    Mode:Managed
                    Frequency=2.437 GHz (Channel 6)
                    Quality:3/5  Signal level:-68 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 06 - Address: 00:23:08:92:38:E8
                    ESSID:"EasyBox-923818"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-91 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: Unknown: DD8E0050F204104A00011010440001021041000100103B00010310470010000000000000000300000023089238E81021000B436F72706F726174696F6E102300094152563735323950571024000932302E30322E3031351042000B52393233303134353638301054000800060050F204000110110014576972656C65737320526F757465722857464129100800020004
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 12 Mb/s
                              24 Mb/s; 48 Mb/s
          Cell 07 - Address: 00:11:6B:15:78:6E
                    ESSID:"default"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-90 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 08 - Address: 00:1D:19:51:B0:AD
                    ESSID:"Arcor-51B049"
                    Mode:Managed
                    Frequency=2.452 GHz (Channel 9)
                    Quality:0/5  Signal level:-91 dBm  Noise level:-90 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 09 - Address: 00:0F:B5:56:A1:F6
                    ESSID:"CIC"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-67 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 10 - Address: 00:04:0E:8E:BB:59
                    ESSID:"WLAN-00040E8EBB59"
                    Mode:Managed
                    Frequency=2.462 GHz (Channel 11)
                    Quality:4/5  Signal level:-64 dBm  Noise level:-88 dBm
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 11 - Address: 00:18:4D:0D:61:AE
                    ESSID:"huhu"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 12 - Address: 00:22:6B:74:F5:40
                    ESSID:"Gamepool"
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-88 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7E0050F204104A0001101044000102103B00010310470010138140001DD211B29FFFC67E816B4BFB102100074C696E6B73797310230006526F7574657210240007575254353447321042000C4353563031484131393230331054000800060050F204000110110011576972656C6573732D4720526F75746572100800020088
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

```

/etc/udev/rules.d/70-persistent-net.rules
```

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:e8:bd:ce:12", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 ()
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:5f:b4:e1:3d", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:5f:b4:e1:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

```

---

### Post by meborc on 2009-10-06
install wicd and try to connect with it... i'm guessing it is NM problem, not the drivers or the card

if wicd works, file a bug against NM

EDIT: also check this - [http://ubuntuforums.org/showthread.php?t=1283847](http://ubuntuforums.org/showthread.php?t=1283847) there seems to be trouble at NM land since last upgrade

---

### Post by SqRt7744 on 2009-10-06
Thanks for the suggestions, I guess I will have to try wicd. It wasn't the name of the interface as I initially suspected, I changed the name to wlan0 and it still won't be taken by networkmanager.

Incidentally, I changed the name by editing the file /etc/udev/rules.d/70-persistent-net.rules to

```

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:24:e8:bd:ce:12", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4315 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:22:5f:b4:e1:3d", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="wlan0"

```

the original can be found in my previous post, basically i deleted an apparently redundant entry and changed the NAME field of the wireless card to wlan0

---

### Post by SqRt7744 on 2009-10-06
wicd totally works, I can't believe it. Thanks for the suggestion meborc :)

---

### Post by meborc on 2009-10-06
> **SqRt7744 said:**
> wicd totally works, I can't believe it. Thanks for the suggestion meborc :)

no problem :)

---

