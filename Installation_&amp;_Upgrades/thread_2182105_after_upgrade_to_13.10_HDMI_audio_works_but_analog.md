---
title: "after upgrade to 13.10 HDMI audio works but analog does not"
date: 2013-10-20
forum: Installation &amp; Upgrades
---

### Post by nazgul17 on 2013-10-20
Hi,

after upgrading from Kubuntu 13.04 to 13.10 I found that the kernel now supported HDMI audio and that is great! On the other hand, now, the analog audio device in gray. The thing is, I often use the notebook with an HDMI monitor and headphones. You could say I can just plug my headphones in the monitor audio out - and you are right - but that is less comfortable.

What is weird is that before the upgrade, the situation was the opposite: HDMI audio was in gray and the only working device was the analog one; now, the gray device is the analog one while HDMI works.


This is what I get executing a couple of commands that I found on Google (I am not very knowledgeable about this kind of commands, I just know the mainstream ones)
```
marco@marco-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
marco@marco-laptop:~$ aplay -L
default
    Playback/recording through the PulseAudio sound server
sysdefault:CARD=PCH
    HDA Intel PCH, ALC269VB Analog
    Default Audio Device
front:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Front speakers
surround40:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
hdmi:CARD=PCH,DEV=0
    HDA Intel PCH, HDMI 0
    HDMI Audio Output
dmix:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct sample mixing device
dmix:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample mixing device
dsnoop:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct sample snooping device
dsnoop:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct sample snooping device
hw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Direct hardware device without any conversions
hw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Direct hardware device without any conversions
plughw:CARD=PCH,DEV=0
    HDA Intel PCH, ALC269VB Analog
    Hardware device with all software conversions
plughw:CARD=PCH,DEV=3
    HDA Intel PCH, HDMI 0
    Hardware device with all software conversions
marco@marco-laptop:~$ sudo -s
root@marco-laptop:~# lspci -v | grep -A7 -i "audio"
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
        Subsystem: ASUSTeK Computer Inc. Device 1ac3
        Flags: bus master, fast devsel, latency 0, IRQ 45
        Memory at df600000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel
 
```

Oh, and I am using an Asus X53Sv, if this can be of any help.


Does anybody know a way to reactivate the old driver as well? Do I need to include any additional information?

---

### Post by nazgul17 on 2013-10-20
Never mind, I found the problem.

It seems like I had to dig into the Multimedia section, Audio and Video Settings, Audio hardware setup and select the profile using the analog device.
Great advancement for my experience since now using the tv for movies is much simpler and has a higher quality with just an HDMI cable!

---

