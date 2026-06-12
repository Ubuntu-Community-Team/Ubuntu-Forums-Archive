---
title: "Should I go back to 12.04 ?"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by squidf on 2013-06-02
Hello all

I installed 1 month ago the 13.04 from 12.10 and I have many issues. I am then wondering whether I need to go back to 12.04LTS.
Here is the story, keeping in mind that everythin was working well with the 12.10 version, despite it seemed heavy for my netbook.
To install a new version, I don't use the upgrade feature. I have separated the partitions for / and /home. So, each time, I format the / partition to install a new version.

I have a netbook Compaq CQ-600. I found Ubuntu heavy for it. So, 1 month ago, I intalled XUbuntu 13.04. The installation was difficult because the wifi connexion was unstable. In fact, the system kept asking me in loops the password to connect. Then, suddently, it worked. I realized later on that the proprietary driver Broadcom BCM4313 was not used anymore by the system as it was stated in  sofware management / proprietary driver that this driver doesn't work.
Finally, my wife preferring Unity to XFCE environnement (and it is her netbook ;)), I decided to install again Ubuntu but in its 13.04 version this time.

The installation of Ubuntu 13.04 was a nightmare because, this time, the system didn't manage to stop using the proprietary driver BCM4313. At least, this is my analysis because even by telling in the Proprietary driver window not to use this BCM4313, the system kept activating it (meaning that going again to this menu, the option to use this BCM driver was activated....).
I had to search the forums and, finally, no proposals worked but I realized that using 

sudo apt-get remove --purge bcmwl-kernel-source 

allowed the system not to use this BCM driver anymore. Then, I succeeded to connect to internet with Ubuntu 13.04 ; but it is not the end of the story....

The connection to internet is not fully stable. Sometimes to time, the system asks me in loops to enter the password for wifi connection but never connects... the "solution" is to remove the past connection in the connection manager menu and to restart the computer, then I am asked to enter the wifi password and it does connect.
For information, if I boot on a Live USB LUbuntu 13.04 session, LUbuntu asks only once the wifi password and the connection is established. If I look in the proprietary driver menu, I can see the BCM4313 driver is seen as not working properly and is not used...
In all cases (ubuntu,Xubuntu,Lubuntu), I have a key on the keyboard to enable or to disable the wifi connection which has a diode. The diode changes color depending on the wifi connection. This diode doesn't work with the 13.04 versions but was working with the 12.xx versions.

This is the story for the unstable wifi connection but I have another issue which is linked to very short battery life. Both with Xubuntu 13.04 and Ubuntu 13.04, I have a battery life time around 1.5 hour and then the netbook just suddently powers off (the battery level is usually at around 25-30% of charge at that time, according to the powermanager icon in the top bar) !
I tested the battery with various softwares and nothing wrong is identified. Moreover, with the 12.xx versions I had around 3 hours of autonomy and I never got this switch off behavior without any notice.

I am really considering to come back to 12.04 but I was really interested by getting the 13.04 which should use less resources and improve the battery life ; but for me, everything is going to the opposite way !

Does someone has an idea how to make the 13.04 working for me ?



Here below are some information on my configuration when I was with XUbuntu 13.04. I can update some of them if you need to, as I am now with Ubuntu 13.04. Let me know.

cat /etc/lsb-release
```
&#65279;
DISTRIB_ID=Ubuntu 
DISTRIB_RELEASE=13.04 
DISTRIB_CODENAME=raring 
DISTRIB_DESCRIPTION="Ubuntu 13.04"
```

lsusb
```

Bus 001 Device 002: ID 5986:0314 Acer, Inc  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
```

lspci
```

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge 
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02) 
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) 
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) 
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) 
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) 
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) 
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) 
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) 
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02) 
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02) 
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01) 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 

```

lspci -nn | grep -i net
```

01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01) 
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) 

```

lspci -k
```

00:00.0 Host bridge: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx DMI Bridge 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: agpgart-intel 
00:02.0 VGA compatible controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: i915 
00:02.1 Display controller: Intel Corporation Atom Processor D4xx/D5xx/N4xx/N5xx Integrated Graphics Controller 
    Subsystem: Hewlett-Packard Company Device 1584 
00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: snd_hda_intel 
00:1c.0 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 1 (rev 02) 
    Kernel driver in use: pcieport 
00:1c.2 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 3 (rev 02) 
    Kernel driver in use: pcieport 
00:1c.3 PCI bridge: Intel Corporation NM10/ICH7 Family PCI Express Port 4 (rev 02) 
    Kernel driver in use: pcieport 
00:1d.0 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: uhci_hcd 
00:1d.1 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: uhci_hcd 
00:1d.2 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: uhci_hcd 
00:1d.3 USB controller: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: uhci_hcd 
00:1d.7 USB controller: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: ehci-pci 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: lpc_ich 
00:1f.2 SATA controller: Intel Corporation NM10/ICH7 Family SATA Controller [AHCI mode] (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: ahci 
00:1f.3 SMBus: Intel Corporation NM10/ICH7 Family SMBus Controller (rev 02) 
    Subsystem: Hewlett-Packard Company Device 1584 
01:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01) 
    Subsystem: Hewlett-Packard Company Device 145c 
    Kernel driver in use: bcma-pci-bridge 
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05) 
    Subsystem: Hewlett-Packard Company Device 1584 
    Kernel driver in use: r8169

```

sudo lshw -C network
```

 *-network                
       description: Network controller 
       produit: BCM4313 802.11b/g/n Wireless LAN Controller 
       fabriquant: Broadcom Corporation 
       identifiant matériel: 0 
       information bus: pci@0000:01:00.0 
       version: 01 
       bits: 64 bits 
       horloge: 33MHz 
       fonctionnalités: pm msi pciexpress bus_master cap_list 
       configuration: driver=bcma-pci-bridge latency=0 
       ressources: irq:16 mémoire:55000000-55003fff 
  *-network 
       description: Ethernet interface 
       produit: RTL8101E/RTL8102E PCI Express Fast Ethernet controller 
       fabriquant: Realtek Semiconductor Co., Ltd. 
       identifiant matériel: 0 
       information bus: pci@0000:03:00.0 
       nom logique: eth0 
       version: 05 
       numéro de série: 78:ac:c0:c6:01:f4 
       taille: 10Mbit/s 
       capacité: 100Mbit/s 
       bits: 64 bits 
       horloge: 33MHz 
       fonctionnalités: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl_nic/rtl8105e-1.fw latency=0 link=no multicast=yes port=MII speed=10Mbit/s 
       ressources: irq:43 portE/S:1000(taille=256) mémoire:52004000-52004fff mémoire:52000000-52003fff 
  *-network 
       description: Interface réseau sans fil 
       identifiant matériel: 2 
       nom logique: wlan0 
       numéro de série: 88:9f:fa:7a:98:10 
       fonctionnalités: ethernet physical wireless 
       configuration: broadcast=yes driver=brcmsmac driverversion=3.8.0-22-generic firmware=N/A ip=192.168.1.134 link=yes multicast=yes wireless=IEEE 802.11bgn
```

lsmod
```

Module                  Size  Used by 
parport_pc             27504  0  
ppdev                  12817  0  
bnep                   17669  2  
rfcomm                 37420  0  
bluetooth             202069  10 bnep,rfcomm 
arc4                   12543  2  
brcmsmac              521468  0  
binfmt_misc            17260  1  
cordic                 12518  1 brcmsmac 
brcmutil               14355  1 brcmsmac 
snd_hda_codec_idt      63896  1  
mac80211              526519  1 brcmsmac 
ip6t_REJECT            12533  1  
cfg80211              436177  2 brcmsmac,mac80211 
xt_hl                  12465  6  
ip6t_rt                12473  3  
snd_hda_intel          38307  6  
nf_conntrack_ipv6      13871  7  
coretemp               13131  0  
nf_defrag_ipv6         13025  1 nf_conntrack_ipv6 
joydev                 17097  0  
ipt_REJECT             12485  1  
hp_wmi                 17712  0  
snd_hda_codec         117580  2 snd_hda_codec_idt,snd_hda_intel 
xt_LOG                 17192  10  
snd_hwdep              13272  1 snd_hda_codec 
sparse_keymap          13658  1 hp_wmi 
snd_pcm                80890  2 snd_hda_codec,snd_hda_intel 
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel 
xt_limit               12541  13  
xt_tcpudp              12531  18  
i915                  535507  4  
xt_addrtype            12563  4  
uvcvideo               71279  0  
snd_seq_midi           13132  0  
videobuf2_vmalloc      12920  1 uvcvideo 
snd_seq_midi_event     14475  1 snd_seq_midi 
nf_conntrack_ipv4      14071  7  
videobuf2_memops       13042  1 videobuf2_vmalloc 
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4 
snd_rawmidi            25114  1 snd_seq_midi 
videobuf2_core         39161  1 uvcvideo 
xt_state               12514  14  
drm_kms_helper         47545  1 i915 
microcode              18286  0  
videodev               95806  2 uvcvideo,videobuf2_core 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi 
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi 
drm                   228750  5 i915,drm_kms_helper 
snd_timer              24411  2 snd_pcm,snd_seq 
ip6table_filter        12711  1  
ip6_tables             17819  1 ip6table_filter 
nf_conntrack_netbios_ns    12585  0  
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns 
nf_nat_ftp             12548  0  
wmi                    18590  1 hp_wmi 
i2c_algo_bit           13197  1 i915 
nf_nat                 24952  1 nf_nat_ftp 
nf_conntrack_ftp       13118  1 nf_nat_ftp 
nf_conntrack           67003  8 nf_nat_ftp,nf_conntrack_netbios_ns,nf_nat,xt_state,nf_conntrack_broadcast,nf_conntrack_ftp,nf_conntrack_ipv4,nf_conntrack_ipv6 
mac_hid                13037  0  
lp                     13299  0  
iptable_filter         12706  1  
ip_tables              17791  1 iptable_filter 
snd                    56485  21 snd_hwdep,snd_timer,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device 
lpc_ich                16925  0  
x_tables               21974  13 ip6table_filter,xt_hl,ip_tables,xt_tcpudp,xt_limit,xt_state,xt_LOG,iptable_filter,ip6t_rt,ipt_REJECT,ip6_tables,xt_addrtype,ip6t_REJECT 
video                  18894  1 i915 
psmouse                81038  0  
soundcore              12600  1 snd 
parport                40753  3 lp,ppdev,parport_pc 
bcma                   39645  1 brcmsmac 
serio_raw              13031  0  
ahci                   25507  3  
libahci                26108  1 ahci 
r8169                  61531  0 

```

iwconfig
```

wlan0     IEEE 802.11bgn  ESSID:"barthol"   
          Mode:Managed  Frequency:2.412 GHz  Access Point: 20:AA:4B:CD:A5:48    
          Bit Rate=72.2 Mb/s   Tx-Power=19 dBm    
          Retry  long limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality=61/70  Signal level=-49 dBm   
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:3  Invalid misc:121   Missed beacon:0 
 
lo        no wireless extensions. 
 
eth0      no wireless extensions. 
 
ifconfig
eth0      Link encap:Ethernet  HWaddr 78:ac:c0:c6:01:f4   
          UP BROADCAST MULTICAST  MTU:1500  Metric:1 
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0 
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 lg file transmission:1000  
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B) 
 
lo        Link encap:Boucle locale   
          inet adr:127.0.0.1  Masque:255.0.0.0 
          adr inet6: ::1/128 Scope:Hôte 
          UP LOOPBACK RUNNING  MTU:65536  Metric:1 
          Packets reçus:640 erreurs:0 :0 overruns:0 frame:0 
          TX packets:640 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 lg file transmission:0  
          Octets reçus:86434 (86.4 KB) Octets transmis:86434 (86.4 KB) 
 
wlan0     Link encap:Ethernet  HWaddr 88:9f:fa:7a:98:10   
          inet adr:192.168.1.134  Bcast:192.168.1.255  Masque:255.255.255.0 
          adr inet6: fe80::8a9f:faff:fe7a:9810/64 Scope:Lien 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          Packets reçus:5910 erreurs:0 :0 overruns:0 frame:0 
          TX packets:4585 errors:0 dropped:0 overruns:0 carrier:0 
          collisions:0 lg file transmission:1000  
          Octets reçus:3390282 (3.3 MB) Octets transmis:780027 (780.0 KB) 

```

sudo iwlist scan
```

wlan0     Scan completed : 
          Cell 01 - Address: 20:AA:4B:CD:A5:48 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=60/70  Signal level=-50 dBm   
                    Encryption key:on 
                    ESSID:"barthol" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000002020df9d156 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000762617274686F6C 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010E4388B86E9A955A3F01CA899B0F7D2D610210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30351042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103 
                    IE: Unknown: DD090010180201F0040000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 02 - Address: 20:AA:4B:CD:A5:4A 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=59/70  Signal level=-51 dBm   
                    Encryption key:off 
                    ESSID:"barthol-guest" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000002020df9dee9 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000D62617274686F6C2D6775657374 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1601081100000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD090010180201F0040000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 03 - Address: 4C:60:DE:D6:1D:C1 
                    Channel:2 
                    Frequency:2.417 GHz (Channel 2) 
                    Quality=36/70  Signal level=-74 dBm   
                    Encryption key:on 
                    ESSID:"Hummingbird" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000eba284b74b 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000B48756D6D696E6762697264 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 030102 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101820003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C334C101BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 2D1A4C101BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C3402080800000000000000000000000000000000000000 
                    IE: Unknown: 3D1602080800000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD0A00037F04010002004000 
                    IE: Unknown: DD7A0050F204104A0001101044000102103B00010310470010000000000000100000004C60DED61DC1102100044E54475210230009776E72323030307633102400016E104200046E6F6E651054000800060050F204000110110016574E5232303030763328576972656C65737320415029100800020086103C000103 
          Cell 04 - Address: C0:C1:C0:A3:07:32 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=48/70  Signal level=-62 dBm   
                    Encryption key:on 
                    ESSID:"Thunderbird" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000003b2287ea78d 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000B5468756E64657262697264 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000 
                    IE: Unknown: DD6E0050F204104A00011010440001021041000100103B00010310470010066051460B8DDC9B65F6F51FC3C13E3D10210005436973636F102300054531323030102400063132333435361042000234321054000800060050F2040001101100054531323030100800020084103C000101 
                    IE: Unknown: DD090010180202F0040000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 05 - Address: 00:23:69:49:99:E0 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=30/70  Signal level=-80 dBm   
                    Encryption key:on 
                    ESSID:"WAGSHOME" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000003b2261b7c6a 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000857414753484F4D45 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 32040C183060 
                    IE: Unknown: 2D1AEC0117FFFF0000000000000000000000000000000C0000000000 
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000 
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
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD07000C4307000000 
                    IE: Unknown: 0706555320010B10 
                    IE: Unknown: DD1E00904C33EC0117FFFF0000000000000000000000000000000C0000000000 
                    IE: Unknown: DD1A00904C3401000500000000000000000000000000000000000000 
                    IE: Unknown: DD820050F204104A0001101044000102103B000103104700102880288028801880A8800023694999E01021000C4C696E6B73797320496E632E102300095752543136304E76321024000776322E302E3032104200033031311054000800060050F2040001101100114C696E6B737973205752543136304E763210080002008C103C000101 
          Cell 06 - Address: 68:7F:74:8C:B6:1F 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=26/70  Signal level=-84 dBm   
                    Encryption key:off 
                    ESSID:"linksys" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000000035cf180 
                    Extra: Last beacon: 860ms ago 
                    IE: Unknown: 00076C696E6B737973 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 030106 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00 
                    IE: Unknown: 2D1A4C101BFF00000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1606001B00000000000000000000000000000000000000 
                    IE: Unknown: DD0900037F01010000FF7F 
                    IE: Unknown: DD0A00037F04010000000000 
                    IE: Unknown: DD0E0050F204104A0001101044000101 
          Cell 07 - Address: 00:1E:E5:39:ED:FF 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=28/70  Signal level=-82 dBm   
                    Encryption key:on 
                    ESSID:"Cisco" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000014535b6183 
                    Extra: Last beacon: 856ms ago 
                    IE: Unknown: 0005436973636F 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 0504FF010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: DD090010180202F4010000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
          Cell 08 - Address: 2C:B0:5D:37:BB:CD 
                    Channel:7 
                    Frequency:2.442 GHz (Channel 7) 
                    Quality=28/70  Signal level=-82 dBm   
                    Encryption key:on 
                    ESSID:"ffbbarnes" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000083127f918e 
                    Extra: Last beacon: 748ms ago 
                    IE: Unknown: 00096666626261726E6573 
                    IE: Unknown: 010882840B162430486C 
                    IE: Unknown: 030107 
                    IE: Unknown: 050401020000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC181FFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1607001700000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD270050F204104A0001101044000102104700106B9567FD3F42F90CF6C2625D699FCBC2103C000103 
                    IE: Unknown: DD090010180204F0040000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 09 - Address: 9C:D3:6D:AC:9D:C6 
                    Channel:6 
                    Frequency:2.437 GHz (Channel 6) 
                    Quality=31/70  Signal level=-79 dBm   
                    Encryption key:on 
                    ESSID:"NETGEAR - Mott" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000003c9a7cded4 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 000E4E455447454152202D204D6F7474 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030106 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1AFC191BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D1606001300000000000000000000000000000000000000 
                    IE: Unknown: DD870050F204104A00011010440001021041000100103B000103104700107F8D9EF742F14C0F9CEF84449AA65A0A1021000D4E4554474541522C20496E632E1023000A574E52333530304C76321024000A574E52333530304C763210420005333530304C1054000800060050F20400011011000A574E52333530304C7632100800020084103C000101 
                    IE: Unknown: DD090010180202F02C0000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
          Cell 10 - Address: 00:18:3A:80:F7:9E 
                    Channel:9 
                    Frequency:2.452 GHz (Channel 9) 
                    Quality=37/70  Signal level=-73 dBm   
                    Encryption key:on 
                    ESSID:"Karla" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000dc41fe805b 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 00054B61726C61 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030109 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD090010180205F0000000 
          Cell 11 - Address: 00:22:3F:34:40:B6 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=22/70  Signal level=-88 dBm   
                    Encryption key:on 
                    ESSID:"NETGEAR" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              12 Mb/s; 24 Mb/s; 36 Mb/s 
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000b74f5cb465 
                    Extra: Last beacon: 168ms ago 
                    IE: Unknown: 00074E455447454152 
                    IE: Unknown: 010882848B960C183048 
                    IE: Unknown: 03010B 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 32041224606C 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
          Cell 12 - Address: CC:B2:55:41:80:0E 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=21/70  Signal level=-89 dBm   
                    Encryption key:on 
                    ESSID:"mekiah10" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000eaaada84e4 
                    Extra: Last beacon: 644ms ago 
                    IE: Unknown: 00086D656B6961683130 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 050400030002 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: DD090010180202F0000000 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
          Cell 13 - Address: 94:44:52:AD:93:55 
                    Channel:1 
                    Frequency:2.412 GHz (Channel 1) 
                    Quality=22/70  Signal level=-88 dBm   
                    Encryption key:on 
                    ESSID:"belkin.3633" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=00000034c3b3e165 
                    Extra: Last beacon: 628ms ago 
                    IE: Unknown: 000B62656C6B696E2E33363333 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 030101 
                    IE: Unknown: 32040C183060 
                    IE: Unknown: 0706555320010B10 
                    IE: Unknown: 33082001020304050607 
                    IE: Unknown: 33082105060708090A0B 
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: 050400010000 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2D1A6E1117FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: 3D1601050700000000000000000000000000000000000000 
                    IE: Unknown: 7F0101 
                    IE: WPA Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: 0B0503001C127A 
                    IE: Unknown: DD1E00904C336E1117FFFF0000010000000000000000000000000C0000000000 
                    IE: Unknown: DD1A00904C3401050700000000000000000000000000000000000000 
                    IE: Unknown: DD07000C4304000000 
          Cell 14 - Address: 00:18:39:84:CC:4B 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=29/70  Signal level=-81 dBm   
                    Encryption key:on 
                    ESSID:"JHome" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000003b225eeafa2 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 00054A486F6D65 
                    IE: Unknown: 010882848B96A4B0C8EC 
                    IE: Unknown: 03010B 
                    IE: Unknown: 2A0104 
                    IE: Unknown: 2F0104 
                    IE: Unknown: 32048C9298E0 
                    IE: Unknown: DD09001018020015000000 
          Cell 15 - Address: 00:1C:DF:39:4F:FA 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=24/70  Signal level=-86 dBm   
                    Encryption key:on 
                    ESSID:"Edwards" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=0000039455cb1153 
                    Extra: Last beacon: 208ms ago 
                    IE: Unknown: 000745647761726473 
                    IE: Unknown: 010882848B961224486C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 32040C183060 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: DD270050F204104A0001101044000102104700102880288028801880A880001CDF394FFA103C000101 
                    IE: Unknown: 050400010119 
                    IE: Unknown: 2A0104 
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD07000C4307000000 
          Cell 16 - Address: E0:91:F5:3D:1D:42 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=23/70  Signal level=-87 dBm   
                    Encryption key:on 
                    ESSID:"EdgarENewbyI-PC-Wireless" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s 
                              9 Mb/s; 12 Mb/s; 18 Mb/s 
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s 
                    Mode:Master 
                    Extra:tsf=000000796f5f3180 
                    Extra: Last beacon: 388ms ago 
                    IE: Unknown: 00184564676172454E65776279492D50432D576972656C657373 
                    IE: Unknown: 010882848B960C121824 
                    IE: Unknown: 03010B 
                    IE: Unknown: 050400010002 
                    IE: Unknown: 070C55532001021B0307140A021B 
                    IE: Unknown: 2A0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: WPA Version 1 
                        Group Cipher : TKIP 
                        Pairwise Ciphers (2) : CCMP TKIP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32043048606C 
                    IE: Unknown: DD180050F2020101020003A4000027A4000042435E0062322F00 
                    IE: Unknown: 2D1A4E1003FF00000000000000000000000000000000000000000000 
                    IE: Unknown: 3D160B0F0800000000000000000000000000000000000000 
                    IE: Unknown: DD0E0050F204104A0001101044000102 
                    IE: Unknown: DD0900037F01010000FF7F 
                    IE: Unknown: DD0A00037F04010000000000 
          Cell 17 - Address: 30:46:9A:50:F5:7E 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=30/70  Signal level=-80 dBm   
                    Encryption key:on 
                    ESSID:"NETGEAR" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s 
                              24 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000003b2240a1635 
                    Extra: Last beacon: 72ms ago 
                    IE: Unknown: 00074E455447454152 
                    IE: Unknown: 010882848B962430486C 
                    IE: Unknown: 03010B 
                    IE: Unknown: 2A0100 
                    IE: Unknown: 2F0100 
                    IE: IEEE 802.11i/WPA2 Version 1 
                        Group Cipher : CCMP 
                        Pairwise Ciphers (1) : CCMP 
                        Authentication Suites (1) : PSK 
                    IE: Unknown: 32040C121860 
                    IE: Unknown: 2D1A7C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: 3D160B081100000000000000000000000000000000000000 
                    IE: Unknown: 4A0E14000A002C01C800140005001900 
                    IE: Unknown: 7F0101 
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700106FA951500855935FF22622447DF35B951021000D4E4554474541522C20496E632E10230008574E44523334303010240008574E4452333430301042000230311054000800060050F204000110110008574E445233343030100800020084103C000103 
                    IE: Unknown: DD090010180200F0050000 
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00 
                    IE: Unknown: DD1E00904C337C181BFFFF000000000000000000000000000000000000000000 
                    IE: Unknown: DD1A00904C340B081100000000000000000000000000000000000000 
          Cell 18 - Address: 00:11:6B:2A:31:A8 
                    Channel:11 
                    Frequency:2.462 GHz (Channel 11) 
                    Quality=24/70  Signal level=-86 dBm   
                    Encryption key:off 
                    ESSID:"Yeah" 
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s 
                              18 Mb/s; 36 Mb/s; 54 Mb/s 
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s 
                    Mode:Master 
                    Extra:tsf=000003b226d109c1 
                    Extra: Last beacon: 264ms ago 
 
lo        Interface doesn't support scanning. 
 
eth0      Interface doesn't support scanning.

```

uname -r -m
```

3.8.0-22-generic i686
```

cat /etc/network/interfaces
```

# interfaces(5) file used by ifup(8) and ifdown(8) 
auto lo 
iface lo inet loopback 

```


nm-tool
```

NetworkManager Tool 
 
State: connected (global) 
 
- Device: eth0 ----------------------------------------------------------------- 
  Type:              Wired 
  Driver:            r8169 
  State:             unavailable 
  Default:           no 
  HW Address:        78:AC:C0:C6:01:F4 
 
  Capabilities: 
    Carrier Detect:  yes 
 
  Wired Properties 
    Carrier:         off 
 
 
- Device: wlan0  [barthol] ----------------------------------------------------- 
  Type:              802.11 WiFi 
  Driver:            brcmsmac 
  State:             connected 
  Default:           yes 
  HW Address:        88:9F:FA:7A:98:10 
 
  Capabilities: 
    Speed:           72 Mb/s 
 
  Wireless Properties 
    WEP Encryption:  yes 
    WPA Encryption:  yes 
    WPA2 Encryption: yes 
 
  Wireless Access Points (* = current AP) 
    Thunderbird:     Infra, C0:C1:C0:A3:07:32, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA WPA2 
    Edwards:         Infra, 00:1C:DF:39:4F:FA, Freq 2462 MHz, Rate 54 Mb/s, Strength 40 WPA 
    NETGEAR:         Infra, 00:22:3F:34:40:B6, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA 
    WAGSHOME:        Infra, 00:23:69:49:99:E0, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2 
    NETGEAR - Mott:  Infra, 9C:D3:6D:AC:9D:C6, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA2 
    Karla:           Infra, 00:18:3A:80:F7:9E, Freq 2452 MHz, Rate 54 Mb/s, Strength 49 WEP 
    barthol-guest:   Infra, 20:AA:4B:CD:A5:4A, Freq 2412 MHz, Rate 54 Mb/s, Strength 87 
    *barthol:        Infra, 20:AA:4B:CD:A5:48, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA WPA2 
    Hummingbird:     Infra, 4C:60:DE:D6:1D:C1, Freq 2417 MHz, Rate 54 Mb/s, Strength 47 WPA2 
    JHome:           Infra, 00:18:39:84:CC:4B, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WEP 
    sabol:           Infra, 00:23:69:63:9B:E1, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA 
    Cisco:           Infra, 00:1E:E5:39:ED:FF, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2 
    mekiah10:        Infra, CC:B2:55:41:80:0E, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA 
    Our House:       Infra, 00:1E:E5:78:E3:5E, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2 
    MOTOROLA-8DEA8:  Infra, 94:CC:B9:0E:1B:AD, Freq 2412 MHz, Rate 54 Mb/s, Strength 19 WPA 
    NETGEAR:         Infra, 30:46:9A:50:F5:7E, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA2 
    mekiah10:        Infra, 00:23:97:DF:4A:AC, Freq 2462 MHz, Rate 54 Mb/s, Strength 19 WEP 
    ffbbarnes:       Infra, 2C:B0:5D:37:BB:CD, Freq 2442 MHz, Rate 54 Mb/s, Strength 30 WPA2 
    EdgarENewbyI-PC-Wireless: Infra, E0:91:F5:3D:1D:42, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2 
    belkin.3633:     Infra, 94:44:52:AD:93:55, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2 
    linksys:         Infra, 68:7F:74:8C:B6:1F, Freq 2437 MHz, Rate 54 Mb/s, Strength 27 
    Yeah:            Infra, 00:11:6B:2A:31:A8, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 
 
  IPv4 Settings: 
    Address:         192.168.1.134 
    Prefix:          24 (255.255.255.0) 
    Gateway:         192.168.1.1 
 
    DNS:             24.89.0.22 
    DNS:             24.89.0.21 
    DNS:             192.168.1.1 

```


sudo rfkill list
```

0: hp-wifi: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no 
1: phy0: Wireless LAN 
    Soft blocked: no 
    Hard blocked: no
```

---

### Post by ahallubuntu on 2013-06-02
~

---

### Post by ibjsb4 on 2013-06-02
If you want the classic look, in terminal:

```
sudo apt-get install gnome-session-fallback
```

---

### Post by squidf on 2013-06-02
Thanks for the feedback. Indeed, going to unity 2D is a good tip ; I will look how to do so. 
This said, the user interface is not a big deal by itself. I don't use my wife's laptop so often. So I will let unity as default. 
The main point is that I was excited by the 13.04 new features and I am now disappointed that things going worse compared to the previous version. 

Any idea on how to make the 13.04 working or should I just wait for the 14.04 LTS ?
If you need anymore info on my configuration to help the development, just let me know.

---

### Post by squidf on 2013-06-03
Strange behavior today...

I started my netbook with a ubuntu 12.04 on live USB and the additional drivers window popped up, asking me to install the Broadcom proprietary driver. Here, there is a difference of behavior with the 13.04 which has never asked this.
What is strange is that after installing the proprietary driver, the wifi connection didn't work better than with 13.04 when the proprietary driver was in use ! It is strange because it used to work on 12.10 and 12.04 ???
What is even stranger is that when I restarted my laptop from the hard disk with Ubuntu 13.04, I got wifi connection issue ; the pop-up window asking wifi password kept popping up ! Even if the Broadcom driver was not in use, according to Software manager. The solution was to delete Internet connection history and to restart, then to reconnect on my network.

Is there anything stored on the hard disk or on the wifi card by the live USB session ? Is there something I need to reset somewhere, impacting my wifi card behavior ?

Thanks for your support.

---

