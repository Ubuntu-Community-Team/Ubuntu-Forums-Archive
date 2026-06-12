---
title: "Problems with AUDIO... (Two cards detected??!)"
date: 2005-04-05
forum: Installation &amp; Upgrades
---

### Post by Francisco on 2005-04-05
Hi,

 I have a weird issue on my ubuntu linux pc, seems like when I hit to play cds it doesn't work, and seems like the system loads two sound modules to the kernel.

 My sound is Intel onboard, but something else is being loaded. Do I need to blacklist such? How?

Thanks

> root@ubuntu:/home/francisco # lsmod
Module                  Size  Used by
i830                   68644  2
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
button                  6936  0
ac                      5132  0
battery                 9740  0
ipv6                  230020  8
af_packet              20872  2
e100                   30208  0
eepro100               28300  0
mii                     4864  2 e100,eepro100
snd_intel8x0           33068  3
snd_ac97_codec         59268  1 snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  2 snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  2 snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  11 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
pci_hotplug            30640  0
ehci_hcd               27780  0
uhci_hcd               29328  0
usbcore               104292  4 ehci_hcd,uhci_hcd
intel_mch_agp          10000  0
intel_agp              20512  1
agpgart                31784  4 intel_mch_agp,intel_agp
rtc                    12216  0
pcspkr                  3816  0
floppy                 54996  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
evdev                   9088  0
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
tsdev                   7168  0
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  1
ide_generic             1664  0
ide_disk               16768  3
piix                   12576  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,piix
unix                   25904  688
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb
root@ubuntu:/home/francisco #
 

 Also, how do I install the MP3 plugin for the music player?

Thanks

---

### Post by tkiesel on 2005-04-08
I'm unsure of how to fix your sound woes, though I'd be interested in hearing anyone's diagnosis. Have you tried using a different output format.  (unsure what they're really called)  ALSA, EMS, etc. ?

To get mp3 and other proprietary codecs, there's a HOWTO at the wonderful [Unofficial Ubuntu Guide](http://ubuntuguide.org/4.10/index.html) site.

---

### Post by Francisco on 2005-04-08
[QUOTE=tkiesel]I'm unsure of how to fix your sound woes, though I'd be interested in hearing anyone's diagnosis. Have you tried using a different output format.  (unsure what they're really called)  ALSA, EMS, etc. ?

To get mp3 and other proprietary codecs, there's a HOWTO at the wonderful [Unofficial Ubuntu Guide](http://ubuntuguide.org/4.10/index.html) site.[/QUOTE]
 alsamixer works...

---

