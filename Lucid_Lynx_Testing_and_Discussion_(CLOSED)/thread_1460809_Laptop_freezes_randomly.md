---
title: "Laptop freezes randomly"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Nano on 2010-04-23
My laptop is brand new (Acer Aspire 5732ZG) and it's giving me headache.
X server randomly freezes and lets me no option but a brute force shutdown.
```

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
04:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
05:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

```  

Any ideas about how to debug, proceed?

Thanks in advance, people

---

### Post by Nano on 2010-04-23
BTW, here's my lsmod output

```

Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
vboxnetadp              5235  0 
joydev                 11072  0 
vboxnetflt             12242  0 
vboxdrv              1768311  2 vboxnetadp,vboxnetflt
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
arc4                    1473  2 
snd_hda_codec_realtek   278890  1 
snd_hda_intel          25645  5 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0
 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
radeon                739595  3 
ath9k                 328829  0 
uvcvideo               62403  0 
snd                    70978  21 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    60815  1 radeon
drm_kms_helper         30742  1 radeon
mac80211              238128  1 ath9k
ath                     9723  1 a
videodev               40486  1 uvcvideo
psmouse                64608  0 
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
serio_raw               4918  0 
atl1c                  32975  0 
drm                   198770  5 radeon,ttm,drm_kms_helper
cfg80211              148386  3 ath9k,mac80211,ath
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
led_class               3732  1 ath9k
i2c_algo_bit            6024  1 radeon
intel_agp              29225  0 
video                  20623  0 
output                  2503  1 video
lp                      9336  0 
parport                37160  2 ppdev,lp
usbhid                 40988  0 
hid                    83376  1 usbhid
ahci                   37646  2 


```

---

### Post by csaket on 2010-04-23
I had a similar issue with my laptop with an ATI 3650 chip.
I ended up using the proprietary fglrx drivers and it resolved my issues.

---

### Post by Nano on 2010-04-23
The problem is that proprietary drivers do not support big screen resolutions and I want to be able to connect my laptop to a big screen.

Anyone else experienced this problem?

---

### Post by csaket on 2010-04-23
might be kms then [http://ubuntuforums.org/showpost.php?p=9001793&postcount=11](http://ubuntuforums.org/showpost.php?p=9001793&postcount=11)

---

### Post by Nano on 2010-04-24
Thanks for the tip, bro'.
I'm applying changes right now.

If it works I owe you a beer, if it doesn't I owe you a beer anyway ;)

---

### Post by Nano on 2010-04-27
It did the trick.
Thank you! I owe you one!

---

### Post by moviemaniac on 2010-04-27
I've got another solution for you if you like KMS:
Drop Lucid's -32 kernel and go for the mainline -34 kernels (currently -rc5) from here: 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/](http://kernel.ubuntu.com/~kernel-ppa/mainline/)
Info: [https://wiki.ubuntu.com/KernelTeam/MainlineBuilds](https://wiki.ubuntu.com/KernelTeam/MainlineBuilds)

These also run stable without any freezes with KMS enabled. The added bonus is that these kernels also support power management for ATI on KMS (just edit your /etc/modprobe.d/radeon-kms.conf so it says **options radeon modeset=1 dynpm=1**)

---

