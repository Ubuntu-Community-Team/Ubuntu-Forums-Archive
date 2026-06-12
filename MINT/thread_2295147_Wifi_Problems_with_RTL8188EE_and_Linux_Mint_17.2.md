---
title: "Wifi Problems with RTL8188EE and Linux Mint 17.2"
date: 2015-09-16
forum: MINT
---

### Post by jasmin3 on 2015-09-16
Dear forum users,
I am trying to work around some wifi issues with my HP Pavilion 15 n029sg with a Realtek RTL8188EE wifi card and I am at the end of my knowledge. I bought the laptop without OS because I didn't want to support windows. I have set up a new OS several times, now its the newest linux mint 17.2 version and the problems always come back. When I install the system I have a wirelss connection. The Network Manager works and I can always connect but the internet is either really slow and doesn't load websites at all. Sometimes it's really fast and then 10min later the problems start again.&nbsp; I thought maybe its a problem with the UEFI bios system but 17.2 has full UEFI support, so maybe it is the RTL card? I have already tried to reinstall it, but I am not a computer crack so I am never sure if I am doing it right.
So here is some info about the system:

```
uname -r -m
3.16.0-38-generic x86_64

```

```
sudo lshw -c network

  *-network               
       Beschreibung: Kabellose Verbindung
       Produkt: RTL8188EE Wireless Network Adapter
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:08:00.0
       Logischer Name: wlan0
       Version: 01
       Seriennummer: 70:18:8b:9b:e0:9a
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress bus_master cap_list ethernet physical wireless
       Konfiguration: broadcast=yes driver=rtl8188ee driverversion=3.16.0-38-generic firmware=N/A ip=192.168.0.44 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       Ressourcen: irq:18 ioport:5000(Größe=256) memory:b5500000-b5503fff
  *-network
       Beschreibung: Ethernet interface
       Produkt: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       Hersteller: Realtek Semiconductor Co., Ltd.
       Physische ID: 0
       Bus-Informationen: pci@0000:09:00.0
       Logischer Name: eth0
       Version: 08
       Seriennummer: a0:48:1c:1b:0c:09
       Größe: 10Mbit/s
       Kapazität: 100Mbit/s
       Breite: 64 bits
       Takt: 33MHz
       Fähigkeiten: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       Konfiguration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       Ressourcen: irq:59 ioport:4000(Größe=256) memory:b5404000-b5404fff memory:b5400000-b5403fff
```


```
iwconfig
eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"zANDER_62/2"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: F4:06:8D:2E:32:EF   
          Bit Rate=7.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

lo        no wireless extensions.
```

```
nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        A0:48:1C:1B:0C:09

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [zANDER_62/2] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8188ee
  State:             connected
  Default:           yes
  HW Address:        70:18:8B:9B:E0:9A

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FBI:             Infra, 4C:21:D0:A9:18:6C, Freq 2412 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    Lehrerzimmer:    Infra, 00:24:B2:27:EE:3E, Freq 2437 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    NETCOLOGNE-0224: Infra, 00:1C:28:10:25:2A, Freq 2432 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    Mach3_MCL:       Infra, D4:21:22:DA:8A:6B, Freq 2437 MHz, Rate 54 Mb/s, Strength 100 WPA2
    zANDER_62/1:     Infra, 88:F7:C7:9C:62:77, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2
    HP-Print-2D-Officejet Pro 8600: Infra, 9C:B6:54:5C:D6:2D, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA2
    *zANDER_62/2:    Infra, F4:06:8D:2E:32:EF, Freq 2412 MHz, Rate 54 Mb/s, Strength 63 WPA2

  IPv4 Settings:
    Address:         192.168.0.44
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
    DNS:             192.168.0.2

  IPv6 Settings:
    Address:         2a02:908:f441:4200:646b:fd2a:43cc:4ba9
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    Address:         2a02:908:f441:4200:7218:8bff:fe9b:e09a
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    Address:         fe80::7218:8bff:fe9b:e09a
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    DNS:             2a02:908:2:110a::12
    DNS:             2a02:908:2:1101::12
  IPv6 Settings:
    Address:         2a02:908:f441:4200:646b:fd2a:43cc:4ba9
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    Address:         2a02:908:f441:4200:7218:8bff:fe9b:e09a
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    Address:         fe80::7218:8bff:fe9b:e09a
    Prefix:          64
    Gateway:         fe80::8af7:c7ff:fec3:da3d

    DNS:             2a02:908:2:110a::12
    DNS:             2a02:908:2:1101::12
```

```
lsmod
Module                  Size  Used by
ctr                    13049  1 
ccm                    17773  1 
bnep                   19624  2 
rfcomm                 69509  0 
bluetooth             446409  10 bnep,rfcomm
6lowpan_iphc           18702  1 bluetooth
binfmt_misc            17468  1 
nls_iso8859_1          12713  1 
uvcvideo               81073  0 
videobuf2_vmalloc      13216  1 uvcvideo
videobuf2_memops       13362  1 videobuf2_vmalloc
videobuf2_core         59104  1 uvcvideo
v4l2_common            15681  1 videobuf2_core
videodev              153793  3 uvcvideo,v4l2_common,videobuf2_core
media                  21903  2 uvcvideo,videodev
arc4                   12608  2 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
dm_multipath           22843  0 
scsi_dh                14882  1 dm_multipath
intel_rapl             18783  0 
x86_pkg_temp_thermal    14205  0 
intel_powerclamp       18823  0 
coretemp               13441  0 
kvm                   452088  0 
crct10dif_pclmul       14307  0 
crc32_pclmul           13133  0 
ghash_clmulni_intel    13230  0 
aesni_intel           152552  2 
aes_x86_64             17131  1 aesni_intel
lrw                    13286  1 aesni_intel
gf128mul               14951  1 lrw
glue_helper            13990  1 aesni_intel
ablk_helper            13597  1 aesni_intel
cryptd                 20359  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17393  0 
rtl8188ee              85387  0 
snd_hda_codec_hdmi     47548  1 
rtl_pci                26690  1 rtl8188ee
serio_raw              13483  0 
rtlwifi                64255  2 rtl_pci,rtl8188ee
snd_hda_codec_realtek    77467  1 
snd_hda_codec_generic    69011  1 snd_hda_codec_realtek
mac80211              652777  3 rtl_pci,rtlwifi,rtl8188ee
lpc_ich                21093  0 
snd_hda_intel          30469  5 
snd_hda_controller     30228  1 snd_hda_intel
snd_hda_codec         139682  5 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
rtsx_pci_ms            18168  0 
memstick               16966  1 rtsx_pci_ms
snd_hwdep              17698  1 snd_hda_codec
cfg80211              494362  2 mac80211,rtlwifi
snd_pcm               104112  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           13564  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30876  1 snd_seq_midi
shpchp                 37047  0 
snd_seq                63074  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29562  2 snd_pcm,snd_seq
hp_accel               26034  0 
hp_wireless            12637  0 
lis3lv02d              20156  1 hp_accel
snd                    79468  21 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
input_polldev          14607  1 lis3lv02d
mei_me                 19696  0 
parport_pc             32741  0 
mei                    87875  1 mei_me
soundcore              15047  2 snd,snd_hda_codec
ppdev                  17671  0 
mac_hid                13227  0 
lp                     17759  0 
parport                42348  3 lp,ppdev,parport_pc
dm_mirror              22135  0 
dm_region_hash         20862  1 dm_mirror
dm_log                 18411  2 dm_region_hash,dm_mirror
rtsx_pci_sdmmc         23043  0 
nouveau              1206535  1 
i915                  906113  6 
psmouse               106610  0 
ahci                   34062  3 
libahci                32424  1 ahci
mxm_wmi                13021  1 nouveau
ttm                    93588  1 nouveau
rtsx_pci               46259  2 rtsx_pci_ms,rtsx_pci_sdmmc
r8169                  71694  0 
mii                    13934  1 r8169
i2c_algo_bit           13413  2 i915,nouveau
drm_kms_helper         61574  2 i915,nouveau
drm                   311018  8 ttm,i915,drm_kms_helper,nouveau
wmi                    19193  3 hp_wmi,mxm_wmi,nouveau
video                  20128  2 i915,nouveau
```




If you need anymore info let me know, I wasn't sure what would help. I really hope someone knows an answer by now, I saw that this problem has occurred in the forum already but no anwers could help me yet...Eveything I learn about linux is also learning by doing since I don't really have any special computer skills, so it would be really nice if your ansers could be "dummy friendly" ;)  I just don't want to go backt to windows, because I always really liked linux on my old laptop (where the internet works perfecty) 
Thanks in advance!
Jasmin

---

### Post by howefield on 2015-09-16
Thread moved to the "*MINT*" forum.

Although you are welcome to post here, supporting and being supported by the [MINT]("http://forums.linuxmint.com/") forums may be a better bet.

---

