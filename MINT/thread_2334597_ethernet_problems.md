---
title: "ethernet problems"
date: 2016-08-20
forum: MINT
---

### Post by retirednottired1953 on 2016-08-20
fresh install of Mint Linux 18... can't install wi-fi drivers because my wired connection (ethernet ) is not connecting.....  i go to network settings i see Wired Cable unplugged... i plug ethernet cable to my router and nothing happens

Broadcom Corporation BCM4311 802.11b/g WLAN (Wireless 1390 Mini-Card


```
ifconfig --
eth0      Linkencap:Ethernet  HWaddr 00:1c:23:a6:6a:99  
          UPBROADCAST MULTICAST  MTU:1500  Metric:1
          RXpackets:0 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000 
          RX bytes:0(0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:17 


lo        Linkencap:Local Loopback  
          inetaddr:127.0.0.1  Mask:255.0.0.0
          inet6addr: ::1/128 Scope:Host
          UPLOOPBACK RUNNING  MTU:65536  Metric:1
          RXpackets:304 errors:0 dropped:0 overruns:0 frame:0
          TXpackets:304 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1 
          RXbytes:24128 (24.1 KB)  TX bytes:24128 (24.1 KB)
```

```
dmesg | grep eth--
[    2.104231] b44:Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    2.124724] b44ssb1:0 eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver00:1c:23:a6:6a:99
[   26.958399] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready
[   26.962110] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready
```

```
lsmod


      Module                 Size  Used by
nls_iso8859_1         16384  1
uvcvideo              77824  0
videobuf2_vmalloc     16384  1 uvcvideo
videobuf2_memops      16384  1 videobuf2_vmalloc
videobuf2_v4l2        28672  1 uvcvideo
videobuf2_core        36864  2 uvcvideo,videobuf2_v4l2
v4l2_common           16384  1 videobuf2_v4l2
videodev             155648  4 uvcvideo,v4l2_common,videobuf2_core,videobuf2_v4l2
media                 24576  2 uvcvideo,videodev
gpio_ich              16384  0
dell_laptop           24576  0
dell_wmi              16384  0
sparse_keymap         16384  1 dell_wmi
dcdbas                16384  1 dell_laptop
input_leds            16384  0
joydev                20480  0
snd_hda_codec_hdmi    49152  1
serio_raw             16384  0
b43                  401408  0
snd_hda_codec_idt     53248  1
dell_smm_hwmon        16384  0
coretemp              16384  0
snd_hda_codec_generic   69632  1 snd_hda_codec_idt
snd_hda_intel         36864  3
r852                  20480  0
snd_hda_codec        118784  4snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_intel
bcma                  49152  1 b43
sm_common             20480  1 r852
mac80211             659456  1 b43
nand                  69632  2 r852,sm_common
snd_hda_core          61440  5snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel
nand_ecc              16384  1 nand
nand_bch              16384  1 nand
bch                   20480  1 nand_bch
nand_ids              12288  1 nand
snd_hwdep             16384  1 snd_hda_codec
r592                  20480  0
lpc_ich               20480  0
mtd                   57344  2 nand,sm_common
snd_pcm               94208  4snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_core
memstick              16384  1 r592
cfg80211             499712  2 b43,mac80211
snd_seq_midi          16384  0
snd_seq_midi_event    16384  1 snd_seq_midi
snd_rawmidi           28672  1 snd_seq_midi
ssb_hcd               16384  0
snd_seq               57344  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device        16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer             32768  2 snd_pcm,snd_seq
snd                   69632  17snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore             16384  1 snd
shpchp                32768  0
mac_hid               16384  0
binfmt_misc           20480  1
parport_pc            32768  0
ppdev                 20480  0
lp                    20480  0
parport               45056  3 lp,ppdev,parport_pc
autofs4               40960  2
btrfs               1003520  0
xor                   28672  1 btrfs
raid6_pq             102400  1 btrfs
dm_mirror             24576  0
dm_region_hash        20480  1 dm_mirror
dm_log                20480  2 dm_region_hash,dm_mirror
uas                   20480  0
usb_storage           57344  2 uas
ahci                  36864  2
i915                1130496  3
firewire_ohci         36864  0
psmouse              118784  0
b44                   36864  0
sdhci_pci             24576  0
firewire_core         65536  1 firewire_ohci
libahci               32768  1 ahci
sdhci                 45056  1 sdhci_pci
pata_acpi             16384  0
i2c_algo_bit          16384  1 i915
drm_kms_helper       131072  1 i915
mii                   16384  1 b44
crc_itu_t             16384  1 firewire_core
syscopyarea           16384  1 drm_kms_helper
ssb                   57344  3 b43,b44,ssb_hcd
sysfillrect           16384  1 drm_kms_helper
sysimgblt             16384  1 drm_kms_helper
fb_sys_fops           16384  1 drm_kms_helper
drm                  311296  5 i915,drm_kms_helper
video                 36864  3 i915,dell_wmi,dell_laptop
wmi                   20480  1 dell_wmi
```

---

### Post by howefield on 2016-08-21
Thread moved to the "*MINT*" forum.

---

### Post by banceu_sergiu_ione on 2016-08-21
Had you try to restart the network-manager and see if it recognize it after?

```
 systemctl restart network-manager 
```

---

