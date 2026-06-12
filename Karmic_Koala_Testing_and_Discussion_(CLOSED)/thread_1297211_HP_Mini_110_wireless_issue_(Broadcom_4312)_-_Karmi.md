---
title: "HP Mini 110 wireless issue (Broadcom 4312) - Karmic Koala beta"
date: 2009-10-21
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by caitlyn-martin on 2009-10-21
I've installed Ubuntu Karmic Koala 9.10 beta side by side with the Ubuntu 8.04 LTS / HP Mi factory install on an HP Mini 100 netbook.  It has a Broadcom 4312 wireless chipset and I have installed the restricted drivers.  The wl driver is being loaded and eth2 is assigned.  However, network manager is not seeing any wireless networks.  Please note that I am using standard Ubuntu, not UNR, at this point.  

Output of lsmod:

```
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_idt      59332  1 
snd_hda_intel          26664  2 
snd_hda_codec          69276  2 snd_hda_codec_idt,snd_hda_intel
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
joydev                 10272  0 
iptable_filter          3100  0 
snd_seq_dummy           2656  0 
ip_tables              11692  1 iptable_filter
snd_seq_oss            28576  0 
x_tables               16544  1 ip_tables
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
usblp                  12636  0 
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
lib80211_crypt_tkip     8636  0 
snd                    59204  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
atl1c                  30848  0 
psmouse                56180  0 
serio_raw               5280  0 
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
lp                      8964  0 
parport                35340  2 ppdev,lp
fbcon                  36544  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
usb_storage            52544  0 
i915                  218824  3 
usbhid                 38208  0 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              26684  1 
agpgart                34988  2 drm,intel_agp
video                  19188  1 i915
output                  2780  1 video

```Output of ifconfig -a

```
eth0      Link encap:Ethernet  HWaddr 18:a9:05:87:65:bc  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::1aa9:5ff:fe87:65bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:319244 errors:0 dropped:0 overruns:0 frame:0
          TX packets:174641 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:476001738 (476.0 MB)  TX bytes:12276717 (12.2 MB)
          Interrupt:26 

eth2      Link encap:Ethernet  HWaddr 0c:60:76:7e:06:49  
          inet6 addr: fe80::e60:76ff:fe7e:649/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9257 (9.2 KB)  TX bytes:9257 (9.2 KB)

```Yes, it works fine under Hardy/Mi.

Any suggestions?

---

### Post by caitlyn-martin on 2009-10-21
OK, it's working.  I received one suggestion from another forum that I remove and reinstall the broadcom-wl and b43-fwcutter packages, which I did.  After that wireless sort of worked, with intermittent but frequent freeze ups.  I've seen that with network-manager before so I replaced it with wicd.  That solved the freeze up problem and wireless is working perfectly.

I've never had particularly good results with network-manager.  I guess I'll stick with wicd.

---

### Post by VMC on 2009-10-21
> **caitlyn-martin said:**
> OK, it's working.  I received one suggestion from another forum that I remove and reinstall the broadcom-wl and b43-fwcutter packages, which I did.  After that wireless sort of worked, with intermittent but frequent freeze ups.  I've seen that with network-manager before so I replaced it with wicd.  That solved the freeze up problem and wireless is working perfectly.

I've never had particularly good results with network-manager.  I guess I'll stick with wicd.

There's been a lot of issues regarding wireless of late. Hopefully someone else will benefit from your findings. Could you kindly mark this topic as solved, unless of course you want to keep it open for further replies.

---

