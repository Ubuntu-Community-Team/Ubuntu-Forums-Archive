---
title: "Printer usb / parallel cable not found by Lucid Lynx"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by johnfrith on 2010-08-09
Samsung ML4500  Parallel printer on USB port only worked under Karmic by adding printer using URI of:  parallel:/dev/usb/lp0
On upgrading to Lucid, printer worked after deleting and re-installing  printer in System > Printing. Than after recent upgrade, system doesn't see printer, says  "printer may not be connected". Any help  appreciated. You can help the environment if you can help me figure this  out, as I won't have to throw it away and buy a new one.

Don't really understand anything below, but posted in case it helps.

```
john@jf:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 045e:00d1 Microsoft Corp. Optical Mouse with Tilt Wheel
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 5986:0241 Acer, Inc 
Bus 002 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
``````
john@jf:~$ dmesg | tail -n10
[   29.864166] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   40.412010] wlan0: no IPv6 routers present
[   54.985999] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   91.541130] __ratelimit: 9 callbacks suppressed
[   91.541133] type=1503 audit(1281041070.652:15):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[   91.541153] type=1503 audit(1281041070.652:16):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  108.031800] type=1503 audit(1281041087.139:17):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  108.031816] type=1503 audit(1281041087.139:18):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  118.430298] type=1503 audit(1281041097.539:19):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
[  118.430314] type=1503 audit(1281041097.539:20):  operation="open"  pid=1039 parent=1 profile="/usr/sbin/cupsd" requested_mask="r::"  denied_mask="r::" fsuid=0 ouid=0 name="/var/run/utmp"
```

---

### Post by clrg on 2010-08-09
Disconnect the printer, remove the driver, reboot, connect the printer, install the driver, and check whether it works.

---

### Post by johnfrith on 2010-08-09
Thanks for posting clrg.

I had 'issues' with the driver when I first moved to linux earlier this year, and now I don't know if I'm using a custom driver, or one provide by Ubuntu, or if it makes a difference. How would I remove the driver? And how would I re-install it if it's not one bundled with Ubuntu?

Here is some output, in case it helps (don't really understand it myself). I've bolded any mention of RTL8187, which MAY be the driver.

```
john@jf:~$ lsmod
Module                  Size  Used by
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_si3054     3396  1 
snd_hda_codec_realtek   203312  1 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  2 
snd_hda_intel          22037  4 
snd_hda_codec          74201  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
i915                  285891  3 
snd_pcm                70886  5 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
**rtl8187                50680  0 **
**mac80211              205146  1 rtl8187**
uvcvideo               57022  0 
snd                    54148  20 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
**cfg80211              126517  2 rtl8187,mac80211**
**eeprom_93cx6            1333  1 rtl8187**
psmouse                63245  0 
jmb38x_ms               7407  0 
serio_raw               3978  0 
memstick                8237  1 jmb38x_ms
drm_kms_helper         29297  1 i915
drm                   163034  4 i915,drm_kms_helper
soundcore               6620  1 snd
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
sdhci_pci               5502  0 
sdhci                  15654  1 sdhci_pci
**led_class               2864  2 rtl8187,sdhci**
intel_agp              24415  2 i915
agpgart                31788  2 drm,intel_agp
i2c_algo_bit            5028  1 i915
video                  17375  1 i915
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
r8169                  34300  0 
mii                     4381  1 r8169
```TIA for any help.

---

### Post by clrg on 2010-08-09
Go to Administration-Printers. Alternatively, run 

```
python /usr/share/system-config-printer/system-config-printer.py

```

in a Terminal. The GUI should be self-explanatory. 

Ubuntu ships with drivers for almost any printer. I've never seen a model not supported by default.

---

### Post by johnfrith on 2010-08-09
> **clrg said:**
> Go to Administration-Printers.

Thanks for that clrg. My understanding is that this routine is for setting up printers, rather than drivers, and as I said in my first post, I've tried deleting the printer, and adding it again, with no improvement!

TIA for any help.

---

### Post by clrg on 2010-08-09
If you set up a new printer using the tool I provided, the driver gets installed. Same for removing.

---

### Post by johnfrith on 2010-08-09
Thanks clrg, but that is what I'd done already, as I said in my first post. I did it again, just to make sure, and it's still showing the same symptoms - system thinks it's not connected.

---

### Post by clrg on 2010-08-10
Sorry, I must've missed that. 

I don't really have a clue about printer diagnosing, to be honest.

If available, check the manufacturer's homepage for a newer driver version. Also, try restarting CUPS (Common Unix Priniting System). 

```
sudo service cupsd restart
```

---

### Post by johnfrith on 2010-08-11
Thanks for posting clrg.

Anyone else any ideas?

---

### Post by johnfrith on 2010-08-23
Last chance to help me avoid throwing out a perfectly good printer!

Even just to help me diagnose the problem would help.

TIA.

---

### Post by clrg on 2010-08-23
Does the printer work when you use a live CD?

---

### Post by johnfrith on 2010-08-23
In the course of trying a live cd's, I found the printer didn't work under Karmic any more, so it wasn't an op sys issue. Most embarrassed, as it turned out to be the cable. It was a new cable, and it had worked for a while, so I thought it unlikely to fail, but I thought wrong!

Thanks clrg, you did help - greatly appreciated.

---

