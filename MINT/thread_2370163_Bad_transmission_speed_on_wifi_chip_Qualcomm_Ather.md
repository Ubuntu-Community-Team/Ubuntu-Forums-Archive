---
title: "Bad transmission speed on wifi chip Qualcomm Atheros (QCA9377)"
date: 2017-08-31
forum: MINT
---

### Post by skullnet on 2017-08-31
I have over 2Mb/s on another devices. (link quality = ~100%) On this machine it's over 300kb/s with very poor signal.

**iwconfig**
```
wlp1s0    IEEE 802.11  ESSID:"NBorodin"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: 54:89:98:2C:B6:05   
          ***Bit Rate=1 Mb/s***   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          **Link Quality=43/70**  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0
```

**lshw -C network**

```
  *-network               
       description: Wireless interface
       product: Qualcomm Atheros
       vendor: Qualcomm Atheros
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlp1s0
       version: 31
       serial: a8:6b:ad:0d:b7:bf
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath10k_pci driverversion=4.12.0-041200-lowlatency firmware=WLAN.TF.1.0-00267-1 ip=192.168.100.14 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:283 memory:d1000000-d11fffff
```

I have the latest firmware from git.

Any suggestions?

---

### Post by praseodym on 2017-08-31
Please show these outputs:
```
lsb_release -a
ifconfig -a
dmesg | grep ath
iwlist chan
sudo iwlist scan
```

---

### Post by skullnet on 2017-08-31
**lsb_release -a**
```
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 18.2 Sonya
Release:    18.2
Codename:    sonya
```
**dmesg**
```

[ 2719.882862] ath10k_pci 0000:01:00.0: enabling device (0000 -> 0002)
[ 2719.885131] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[ 2720.099259] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1028:1810
[ 2720.099261] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 2720.099828] ath10k_pci 0000:01:00.0: firmware ver WLAN.TF.1.0-00267-1 api 5 features ignore-otp crc32 79cea2c7
[ 2720.161803] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[ 2720.645721] ath10k_pci 0000:01:00.0: htt-ver 3.1 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[ 2720.650796] ath: EEPROM regdomain: 0x6c
[ 2720.650797] ath: EEPROM indicates we should expect a direct regpair map
[ 2720.650799] ath: Country alpha2 being used: 00
[ 2720.650799] ath: Regpair used: 0x6c
[ 2720.705535] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[ 2721.606695] ath10k_pci 0000:01:00.0: no channel configured; ignoring frame(s)!
[ 2726.370911] ath10k_pci 0000:01:00.0: no channel configured; ignoring frame(s)!
[ 2726.473783] ath10k_pci 0000:01:00.0: no channel configured; ignoring frame(s)!
[ 2731.176431] ath: EEPROM regdomain: 0x809c
[ 2731.176432] ath: EEPROM indicates we should expect a country code
[ 2731.176433] ath: doing EEPROM country->regdmn map search
[ 2731.176434] ath: country maps to regdmn code: 0x52
[ 2731.176434] ath: Country alpha2 being used: CN
[ 2731.176435] ath: Regpair used: 0x52
[ 2731.176436] ath: regdomain 0x809c dynamically updated by country IE
[ 4481.730197] ath10k_pci 0000:01:00.0: pci irq msi oper_irq_mode 2 irq_mode 0 reset_mode 0
[ 4481.988474] ath10k_pci 0000:01:00.0: qca9377 hw1.1 target 0x05020001 chip_id 0x003821ff sub 1028:1810
[ 4481.988478] ath10k_pci 0000:01:00.0: kconfig debug 0 debugfs 1 tracing 1 dfs 0 testmode 0
[ 4481.989292] ath10k_pci 0000:01:00.0: firmware ver WLAN.TF.1.0-00002-QCATFSWPZ-5 api 5 features ignore-otp crc32 c3e0d04f
[ 4482.074954] ath10k_pci 0000:01:00.0: board_file api 2 bmi_id N/A crc32 8aedfa4a
[ 4482.696619] ath10k_pci 0000:01:00.0: htt-ver 3.44 wmi-op 4 htt-op 3 cal otp max-sta 32 raw 0 hwcrypto 1
[ 4482.701721] ath: EEPROM regdomain: 0x6c
[ 4482.701723] ath: EEPROM indicates we should expect a direct regpair map
[ 4482.701725] ath: Country alpha2 being used: 00
[ 4482.701726] ath: Regpair used: 0x6c
[ 4482.704245] ath10k_pci 0000:01:00.0 wlp1s0: renamed from wlan0
[ 4493.311764] ath: EEPROM regdomain: 0x809c
[ 4493.311766] ath: EEPROM indicates we should expect a country code
[ 4493.311767] ath: doing EEPROM country->regdmn map search
[ 4493.311768] ath: country maps to regdmn code: 0x52
[ 4493.311769] ath: Country alpha2 being used: CN
[ 4493.311770] ath: Regpair used: 0x52
[ 4493.311771] ath: regdomain 0x809c dynamically updated by country IE

```
**iwlist chan**
```

wlp1s0    26 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.422 GHz (Channel 3)

```
**iwlist scan**
```

wlp1s0    Scan completed :
          Cell 01 - Address: 54:89:98:2C:B6:05
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"NBorodin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009af33862d
                    Extra: Last beacon: 319ms ago
                    IE: Unknown: 00084E426F726F64696E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACC131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706434E20010D14
          Cell 02 - Address: 34:08:04:91:60:D4
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:on
                    ESSID:"szt18"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001881df1503c
                    Extra: Last beacon: 4378ms ago
                    IE: Unknown: 0005737A743138
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1017FFFF0000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601050600000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05010014127A
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706525520010D10
                    IE: Unknown: DDA70050F204104A0001101044000101103B00010310470010BC329E001DD811B286013408049160D41021001852616C696E6B20546563686E6F6C6F67792C20436F72702E1023001C52616C696E6B20576972656C6573732041636365737320506F696E74102400065254323836301042000831323334353637381054000800060050F20400011011000952616C696E6B41505310080002210C103C0001001049000600372A000120
          Cell 03 - Address: B8:A3:86:1E:C4:D0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"91-24"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001882007273a
                    Extra: Last beacon: 4293ms ago
                    IE: Unknown: 000539312D3234
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1601000000000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101030003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000015127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706525520010E10
          Cell 04 - Address: 54:89:98:2C:AC:B6
                    Channel:4
                    Frequency:2.427 GHz (Channel 4)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"home21"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000005b6e62380f
                    Extra: Last beacon: 4075ms ago
                    IE: Unknown: 0006686F6D653231
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030104
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACC131BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1604080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706434E20010D14
          Cell 05 - Address: 60:A4:4C:A2:FE:D4
                    Channel:8
                    Frequency:2.447 GHz (Channel 8)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"nates"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001881f656951
                    Extra: Last beacon: 3521ms ago
                    IE: Unknown: 00056E61746573
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030108
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000013127A
                    IE: Unknown: DD07000C4307000000
                    IE: Unknown: 0706525520010D10
          Cell 06 - Address: 18:A6:F7:D2:DE:42
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"005"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000875d268eb3
                    Extra: Last beacon: 3446ms ago
                    IE: Unknown: 0003303035
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AEF111BFFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D16090F0000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD9A0050F204104A0001101044000102103B00010310470010000102030405060708090A0B0C0D0E0F1021000754502D4C494E4B10230009544C2D57523834314E1024000431312E3010420003312E301054000800060050F204000110110019576972656C65737320526F7574657220544C2D57523834314E100800020086103C000101104900140024E26002000101600000020001600100020001
          Cell 07 - Address: 10:BF:48:4A:1D:D4
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"Boni"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000001881f340133
                    Extra: Last beacon: 3352ms ago
                    IE: Unknown: 0004426F6E69
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 03010B
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706474220010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010002
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000
                    IE: Unknown: 3D160B000000000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000005127A
                    IE: Unknown: DD07000C4307000000
          Cell 08 - Address: CC:B2:55:9C:11:D8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"D-Link 615 router"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000c04fd94526
                    Extra: Last beacon: 3341ms ago
                    IE: Unknown: 0011442D4C696E6B2036313520726F75746572
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080000000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD800050F204104A0001101044000102103B00010310470010D96C7EFC2F8938F1EFBD6E5148BFA8121021000842726F6164636F6D1023000842726F6164636F6D1024000631323334353610420004303031351054000800060050F20400011011000A42726F6164636F6D4150100800022008103C0001011049000600372A000120
                    IE: Unknown: DD090010180200F00C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

```
**ifconfig**
```

wlp1s0    Link encap:Ethernet  HWaddr a8:6b:ad:0d:b7:bf  
          inet addr:192.168.100.14  Bcast:192.168.100.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:678 errors:0 dropped:3 overruns:0 frame:0
          TX packets:90 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:85494 (85.4 KB)  TX bytes:8500 (8.5 KB)

```

In short: nothing interesting.

---

### Post by ajgreeny on 2017-08-31
*Thread moved to **MINT**.* which is more appropriate and a better fit.

---

### Post by praseodym on 2017-08-31
Change the encryption mod in your router to pure WPA2-AES (CCMP), no mixed mode WPA/WPA2. Also use a fixed channel.

---

### Post by skullnet on 2017-08-31
I did that over 5 years ago when I configured my router.

Also, you may enjoy the performance.
[https://www.youtube.com/watch?v=wNZ0yaEe-Fg&feature=youtu.be](https://www.youtube.com/watch?v=wNZ0yaEe-Fg&feature=youtu.be)

---

### Post by praseodym on 2017-08-31
```
          Cell 01 - Address: 54:89:98:2C:B6:05
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"NBorodin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000009af33862d
                    Extra: Last beacon: 319ms ago
                    IE: Unknown: 00084E426F726F64696E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/[COLOR="#FF0000"]WPA2 Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: [COLOR="#FF0000"]WPA Version 1[/COLOR]
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACC131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603080800000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706434E20010D14
```
It shows mixed mode. Maybe a reset or loss of power?!

---

### Post by skullnet on 2017-08-31
```

wlp1s0    Scan completed :
          Cell 01 - Address: 54:89:98:2C:B6:05
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=48/70  Signal level=-62 dBm  
                    Encryption key:on
                    ESSID:"NBorodin"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000000a3745dd1
                    Extra: Last beacon: 1154ms ago
                    IE: Unknown: 00084E426F726F64696E
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030103
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: DD180050F2020101050003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1ACC131BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1603001B00000000000000000000000000000000000000
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD0A00037F04010020000000
                    IE: Unknown: 0706434E20010D14

```

Fixed this but I didn't notice any change.

---

### Post by praseodym on 2017-08-31
Which country do you live?

---

### Post by skullnet on 2017-09-01
Russia.

---

### Post by praseodym on 2017-09-01
So, then run
```

sudo sed -i "s/REGDOMAIN=/REGDOMAIN=RU/g" /etc/default/crda 
```
Reboot.

---

### Post by skullnet on 2017-09-04
It doesn't make sense because REGDOMAIN was identified as RU by default.

Well, I still have Bit Rate=1 Mb/s (is it normal?) and poor link quality.

---

