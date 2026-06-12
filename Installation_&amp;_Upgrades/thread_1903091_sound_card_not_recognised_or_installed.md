---
title: "sound card not recognised or installed"
date: 2012-01-01
forum: Installation &amp; Upgrades
---

### Post by bolkonski on 2012-01-01
Hi Guys, I-d appreciate a bit of help. I re/installed 11.04 and found that my sound card is not being detected. Here are the system specs.   I-d be grateful for any assistance.
Best wishes
bolkonski
!!################################ !!ALSA Information Script v 0.4.60 !!################################  !!Script ran on: Sun Jan  1 20:40:32 UTC 2012   !!Linux Distribution !!------------------  Ubuntu 11.04 \n \l DISTRIB_ID=Ubuntu DISTRIB_DESCRIPTION="Ubuntu 11.04"   !!DMI Information !!---------------  Manufacturer:      MEDIONPC Product Name:      MS-7366 Product Version:   2.2   !!Kernel Information !!------------------  Kernel release:    2.6.39-020639rc4-generic Operating System:  GNU/Linux Architecture:      i686 Processor:         i686 SMP Enabled:       Yes   !!ALSA Version !!------------  Driver version:      Library version:    1.0.24.1 Utilities version:  1.0.24.2   !!Loaded ALSA modules !!-------------------    !!Sound Servers on this system !!----------------------------  Pulseaudio:       Installed - Yes (/usr/bin/pulseaudio)       Running - Yes  ESound Daemon:       Installed - Yes (/usr/bin/esd)       Running - No   !!Soundcards recognised by ALSA !!-----------------------------    !!PCI Soundcards installed in the system !!--------------------------------------  00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)   !!Advanced information - PCI Vendor/Device/Subsystem ID's !!--------------------------------------------------------  00:09.0 0403: 10de:07fc (rev a1)         Subsystem: 1462:736a   !!Modprobe options (Sound related) !!--------------------------------  snd-atiixp-modem: index=-2 snd-intel8x0m: index=-2 snd-via82xx-modem: index=-2 snd-usb-audio: index=-2 snd-usb-caiaq: index=-2 snd-usb-ua101: index=-2 snd-usb-us122l: index=-2 snd-usb-usx2y: index=-2 snd-cmipci: mpu_port=0x330 fm_port=0x388 snd-pcsp: index=-2 snd-usb-audio: index=-2   !!Loaded sound module options !!--------------------------   !!ALSA Device nodes !!-----------------    !!Aplay/Arecord output !!------------  APLAY  aplay: device_list:240: no soundcards found...  ARECORD  arecord: device_list:240: no soundcards found...  !!Amixer output !!-------------   !!Alsactl output !!-------------  --startcollapse-- --endcollapse--   !!All Loaded Modules !!------------------  Module usb_storage usbhid hid uas ahci firewire_ohci libahci forcedeth firewire_core crc_itu_t pata_amd   !!ALSA/HDA dmesg !!------------------

---

### Post by bolkonski on 2012-01-01
Hey Guys,
i suddenly realised that the info below will bw useful.
Thanks again
bolkonski


aplay: device_list:240: no soundcards found... 
 

  no soundcards found... 
 steve@steve-MS-7366:~$ lspci -v | grep -A7 -i "audio" 
 00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1) 
 	Subsystem: Micro-Star International Co., Ltd. Device 736a 
 	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 7 
 	Memory at fea78000 (32-bit, non-prefetchable) [size=16K] 
 	Capabilities: <access denied> 
  
 00:0a.0 PCI bridge: nVidia Corporation MCP73 PCI Express bridge (rev a1) (prog-if 01 [Subtractive decode]) 
 	Flags: bus master, 66MHz, fast devsel, latency 0

---

