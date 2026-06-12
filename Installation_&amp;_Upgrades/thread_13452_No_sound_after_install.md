---
title: "No sound after install"
date: 2005-01-31
forum: Installation &amp; Upgrades
---

### Post by BenRosey on 2005-01-31
I am new to linux and don't know too much.  After installing ubuntu, I have no sound.  I'm not sure what to do to resolve the issue.

Any help you can provide would be greatly appreciated.

I don't have alsaconf installed.

Here is the output of lsmod:

Module                  Size  Used by
joydev                  9536  0
usbhid                 28864  0
isofs                  33976  0
udf                    79876  0
orinoco_cs              9096  1
orinoco                38284  1 orinoco_cs
hermes                  7936  2 orinoco_cs,orinoco
i830                   68388  3
proc_intf               3968  0
cpufreq_powersave       2048  0
cpufreq_userspace       5336  0
freq_table              4356  0
ipv6                  230020  8
ds                     17796  5 orinoco_cs
button                  6936  0
ac                      5132  0
battery                 9740  0
af_packet              20872  2
yenta_socket           19328  1
pcmcia_core            63156  3 orinoco_cs,ds,yenta_socket
snd_intel8x0m          18632  0
snd_intel8x0           33068  4
snd_ac97_codec         59268  2 snd_intel8x0m,snd_intel8x0
snd_pcm_oss            48168  0
snd_mixer_oss          16640  3 snd_pcm_oss
snd_pcm                85540  4 snd_intel8x0m,snd_intel8x0,snd_pcm_oss
snd_timer              23172  1 snd_pcm
snd_page_alloc         11144  3 snd_intel8x0m,snd_intel8x0,snd_pcm
gameport                4736  1 snd_intel8x0
snd_mpu401_uart         7296  1 snd_intel8x0
snd_rawmidi            23232  1 snd_mpu401_uart
snd_seq_device          7944  1 snd_rawmidi
snd                    50660  13 snd_intel8x0m,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9824  3 snd
pciehp                 83948  0
shpchp                 87276  0
pci_hotplug            30640  2 pciehp,shpchp
uhci_hcd               29328  0
usbcore               104292  4 usbhid,uhci_hcd
intel_agp              20512  1
agpgart                31784  4 intel_agp
floppy                 54996  0
pcspkr                  3816  0
rtc                    12216  0
md                     44744  0
dm_mod                 51068  1
capability              4872  0
commoncap               7168  1 capability
parport_pc             32064  1
lp                     10436  0
parport                37320  2 parport_pc,lp
ide_cd                 38276  0
cdrom                  35872  1 ide_cd
evdev                   9088  0
tsdev                   7168  0
mousedev               10124  1
psmouse                17800  0
reiserfs              207600  1
ext3                  109544  0
jbd                    54552  1 ext3
ide_generic             1664  0
ide_disk               16768  3
piix                   12576  1
ide_core              125272  4 ide_cd,ide_generic,ide_disk,piix
unix                   26160  712
fan                     4236  0
thermal                13200  0
processor              17712  1 thermal
font                    8576  0
vesafb                  6688  0
cfbcopyarea             3968  1 vesafb
cfbimgblt               3200  1 vesafb
cfbfillrect             3712  1 vesafb

---

