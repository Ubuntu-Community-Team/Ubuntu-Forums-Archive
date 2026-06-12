---
title: "Upgraded 10.10, lost sound"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by mlhudson on 2010-10-11
Kernel doesn't seem to be right. Sound was working, but now no sound.

Ran alsa-info.sh, returned:
> !!################################
!!ALSA Information Script v 0.4.59
!!################################

!!Script ran on: Mon Oct 11 13:25:49 UTC 2010

!!Linux Distribution
!!------------------

Ubuntu 10.10 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 10.10"

!!DMI Information
!!---------------

Manufacturer: Acer
Product Name: Aspire 7736

!!Kernel Information
!!------------------

Kernel release: 2.6.35-22-generic
Operating System: GNU/Linux
Architecture: i686
Processor: unknown
SMP Enabled: Yes

!!ALSA Version
!!------------

Driver version:
Library version: 1.0.23
Utilities version: 1.0.23

!!Loaded ALSA modules
!!-------------------

!!Sound Servers on this system
!!----------------------------

Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - Yes

ESound Daemon:
      Installed - Yes (/usr/bin/esd)
      Running - No

!!Soundcards recognised by ALSA
!!-----------------------------

!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

!!Advanced information - PCI Vendor/Device/Susbsystem ID's
!!--------------------------------------------------------

00:1b.0 0403: 8086:293e (rev 03)
 Subsystem: 1025:0296

!!Modprobe options (Sound related)
!!--------------------------------

snd-atiixp-modem: index=-2
snd-intel8x0m: index=-2
snd-via82xx-modem: index=-2
snd-usb-audio: index=-2
snd-usb-caiaq: index=-2
snd-usb-ua101: index=-2
snd-usb-us122l: index=-2
snd-usb-usx2y: index=-2
snd-cmipci: mpu_port=0x330 fm_port=0x388
snd-pcsp: index=-2
snd-usb-audio: index=-2

!!Loaded sound module options
!!--------------------------

!!ALSA Device nodes
!!-----------------

!!Aplay/Arecord output
!!------------

APLAY

aplay: device_list:235: no soundcards found...

ARECORD

arecord: device_list:235: no soundcards found...

!!Amixer output
!!-------------

!!Alsactl output
!!-------------

--startcollapse--
--endcollapse--

!!All Loaded Modules
!!------------------

Module
binfmt_misc
parport_pc
ppdev
joydev
arc4
i915
drm_kms_helper
ath9k
drm
ath9k_common
ath9k_hw
ath
mac80211
acer_wmi
uvcvideo
gspca_zc3xx
gspca_main
usblp
videodev
v4l1_compat
cfg80211
intel_agp
psmouse
serio_raw
led_class
i2c_algo_bit
soundcore
agpgart
video
output
lp
parport
usbhid
hid
ahci
libahci
tg3

!!ALSA/HDA dmesg
!!------------------

Then checked the hardware with
```
lspci -v | less
```
which returned
> 00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Device 0296
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f4700000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

Not sure what I need to do to get sound again. In 10.04, my system worked after using newer Alsa drivers, which seem to be in the current kernel now. But, I'm not sure how I've wonked things. 

My machine is an Acer Aspire 7736z w/ HDA Intel (maybe Realtek 888--that's what it used to show)

Can someone help?

---

