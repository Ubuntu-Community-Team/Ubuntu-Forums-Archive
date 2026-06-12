---
title: "Hang during booting sometimes kubuntu 13.04"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by josvanr on 2013-06-26
Hello

On kubuntu 13.04 sometimes doesnt boot properly: when I view the messages during booting (with f12) the flow of messages stops at some point and nothing happens for a couple of minutes. Then the kde startup screen appears (with the harddisk icons etc) but this hangs after showing the harddisk. ... 

I will include the last parts of dmesg log files in this mail, the first one of a normal boot, the second one of a boot that hanged. (adding attatchments doesnt work for some reason)



Josvanr


dmesg of working boot---------------------------------------------------------------------------------------------

e: CPU4 sig=0x206a7, pf=0x10, revision=0x1a
[   16.062339] microcode: CPU5 sig=0x206a7, pf=0x10, revision=0x1a
[   16.065279] microcode: CPU6 sig=0x206a7, pf=0x10, revision=0x1a
[   16.068482] microcode: CPU7 sig=0x206a7, pf=0x10, revision=0x1a
[   16.071445] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   16.129688] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   16.129697] Copyright(c) 2003-2012 Intel Corporation
[   16.129935] iwlwifi 0000:02:00.0: irq 54 for MSI/MSI-X
[   16.170471] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   16.204858] cfg80211: World regulatory domain updated:
[   16.204867] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.204873] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.204877] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.204882] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.204886] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.204890] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.280504] Linux video capture interface: v2.00
[   16.356427] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   16.356437] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   16.356442] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   16.356446] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   16.356451] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   16.356457] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 ABG, REV=0x74
[   16.356543] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   16.363375] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   16.422157] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   16.481609] uvcvideo: Found UVC 1.00 device HP ENVY HD Webcam (064e:c210)
[   16.627957] input: HP ENVY HD Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
[   16.628115] usbcore: registered new interface driver uvcvideo
[   16.628120] USB Video Class driver (1.1.1)
[   16.708497] snd_hda_intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[   16.838272] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.838467] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.838611] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.838745] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.839441] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.839632] snd_hda_intel 0000:01:00.1: irq 56 for MSI/MSI-X
[   16.842191] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   16.934341] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0x5a0400, board id: 3655, fw id: 648573
[   16.986801] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   17.587546] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   17.951268] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   19.025790] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   19.191163] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[   19.230663] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   19.292096] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   19.352381] init: failsafe main process (1017) killed by TERM signal
[   19.734457] type=1400 audit(1372238930.669:8): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1116 comm="apparmor_parser"
[   19.735529] type=1400 audit(1372238930.669:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1116 comm="apparmor_parser"
[   19.736107] type=1400 audit(1372238930.669:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1116 comm="apparmor_parser"
[   19.737818] type=1400 audit(1372238930.673:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1119 comm="apparmor_parser"
[   19.955820] Bluetooth: RFCOMM TTY layer initialized
[   19.955830] Bluetooth: RFCOMM socket layer initialized
[   19.955831] Bluetooth: RFCOMM ver 1.11
[   19.981250] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.981252] Bluetooth: BNEP filters: protocol multicast
[   19.981258] Bluetooth: BNEP socket layer initialized
root@hpux:/tmp# 













dmesg of failed boot-------------------------------------------------------------------------------




icrocode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   17.425517] cfg80211: World regulatory domain updated:
[   17.425526] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   17.425532] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.425537] cfg80211:   (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.425541] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   17.425546] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.425550] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   17.527716] Intel(R) Wireless WiFi driver for Linux, in-tree:
[   17.527729] Copyright(c) 2003-2012 Intel Corporation
[   17.527965] iwlwifi 0000:02:00.0: irq 54 for MSI/MSI-X
[   17.534925] Linux video capture interface: v2.00
[   17.590700] iwlwifi 0000:02:00.0: loaded firmware version 9.221.4.1 build 25532
[   17.668971] uvcvideo: Found UVC 1.00 device HP ENVY HD Webcam (064e:c210)
[   17.779245] snd_hda_intel 0000:00:1b.0: irq 55 for MSI/MSI-X
[   17.815221] input: HP ENVY HD Webcam as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.5/2-1.5:1.0/input/input8
[   17.815386] usbcore: registered new interface driver uvcvideo
[   17.815391] USB Video Class driver (1.1.1)
[   17.897022] input: HDA Intel PCH HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   17.897314] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   17.897480] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   17.897780] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   17.898922] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   17.899090] snd_hda_intel 0000:01:00.1: irq 56 for MSI/MSI-X
[   17.899919] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUG disabled
[   17.899930] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[   17.899954] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[   17.899963] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_DEVICE_TESTMODE enabled
[   17.899970] iwlwifi 0000:02:00.0: CONFIG_IWLWIFI_P2P disabled
[   17.899980] iwlwifi 0000:02:00.0: Detected Intel(R) Centrino(R) Advanced-N 6200 ABG, REV=0x74
[   17.900061] iwlwifi 0000:02:00.0: L1 Enabled; Disabling L0S
[   17.902394] input: HD-Audio Generic HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   17.906932] iwlwifi 0000:02:00.0: RF_KILL bit toggled to enable radio.
[   17.943026] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   18.094806] psmouse serio1: synaptics: Touchpad model: 1, fw: 7.4, id: 0x1e0b1, caps: 0xd04773/0xe40000/0x5a0400, board id: 3655, fw id: 648573
[   18.145108] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input14
[   19.669020] EXT4-fs (sda9): re-mounted. Opts: errors=remount-ro
[   19.804588] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   20.088886] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   20.376776] EXT4-fs (sda10): mounted filesystem with ordered data mode. Opts: (null)
[   20.430665] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[   20.470367] EXT4-fs (sda7): mounted filesystem with ordered data mode. Opts: (null)
[   20.488764] init: failsafe main process (1025) killed by TERM signal
[   20.793602] type=1400 audit(1372238696.740:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1118 comm="apparmor_parser"
[   20.793935] type=1400 audit(1372238696.740:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1118 comm="apparmor_parser"
[   20.794115] type=1400 audit(1372238696.740:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1118 comm="apparmor_parser"
[   20.794148] type=1400 audit(1372238696.740:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1121 comm="apparmor_parser"
[   20.794521] type=1400 audit(1372238696.740:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1121 comm="apparmor_parser"
[   20.865741] type=1400 audit(1372238696.812:10): apparmor="STATUS" operation="profile_load" name="/usr/sbin/tcpdump" pid=1124 comm="apparmor_parser"
[   20.872686] type=1400 audit(1372238696.820:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1117 comm="apparmor_parser"

root@hpux:/tmp#

---

### Post by TheFu on 2013-06-26
Wish I had the answer.  All that I can suggest are:
* check all the log files for more hints on any issues.
* lots of hardware issues can cause this behavior. I'd look at the power supply, RAM, disks, disk controller, and SATA cables.  Reseat everything.
* ensure you have perfect, versioned backups. A sick system can fail completely at any point.
* Lazy bits on the HDD. I believe that bits which haven't been refreshed actually lose some of their readability over time. A re-write of the bits can solve that and give the HDD an opportunity to discover failing disk sectors that need to be relocated. That happens automatically.

Hopefully, the other log files will show some errors/warning that can lead to the root cause.  [http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files](http://blog.jdpfu.com/2013/02/11/linux-troubleshooting-101-log-files)

Good luck.

---

### Post by josvanr on 2013-06-26
thnx I didnt think of other logs.. I had a look in kern.log and (see below) seems to be a problem.

Some searching lead to a bug but hasnt been resolved yet unfortunately..........


:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 23:10:17 hpux kernel: [   37.361320] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing D582 (len 72, WS 0, PS 0) @ 0xD5B1
Jun 26 23:10:22 hpux kernel: [   42.363726] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 23:10:22 hpux kernel: [   42.363732] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing D1F6 (len 62, WS 0, PS 0) @ 0xD212
Jun 26 23:10:27 hpux kernel: [   47.366154] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 23:10:27 hpux kernel: [   47.366159] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing D1F6 (len 62, WS 0, PS 0) @ 0xD212
Jun 26 23:10:32 hpux kernel: [   52.368555] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 23:10:32 hpux kernel: [   52.368559] [drm:atom_execute_table_locked] *ERROR* atombios stuck executing D1F6 (len 62, WS 0, PS 0) @ 0xD212
Jun 26 23:10:37 hpux kernel: [   57.370970] [drm:atom_op_jump] *ERROR* atombios stuck in loop for more than 5secs aborting
Jun 26 23:10:37 hpux kernel: [   57.370976] [drm:ato

---

### Post by TheFu on 2013-06-27
Well, again, I haven't a clue, but did you google those specific strings?

The "hpux kernel" is concerning, unless hpux is the hostname.  HP-UX is an OS that doesn't run on Intelx86 hardware. It runs on either PA-RISC or Itanium CPUs.  Combined with an AtomBios error that just doesn't make sense.  Last the DRM messages having me thinking there is HDCP hardware failing, but again, I haven't any clue whatsoever.

---

### Post by josvanr on 2013-07-01
It's the host name :) 

After some googeling it seems to be a vgaswitcheroo problem . I use it to turn off the discrete graphics card at startup because otherwise my laptop overheats. But that seems to be a problem. If I dont do that, booting works fine...

---

