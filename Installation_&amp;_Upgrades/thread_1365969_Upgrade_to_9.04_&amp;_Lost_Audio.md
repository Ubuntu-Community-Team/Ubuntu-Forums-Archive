---
title: "Upgrade to 9.04 &amp; Lost Audio"
date: 2009-12-27
forum: Installation &amp; Upgrades
---

### Post by paragonconcept on 2009-12-27
im trying to get alsa working under ubuntu 9.10

im running Advanced Linux Sound Architecture Driver Version 1.0.22

when i run alsaconf it finds my soundcard

but when i run alsamixer - or gnome-alsamixer it doesn't show any channels - it just has a tab for Nvidia MPC78 HDMI and there are no channels in it

It does have a check a for IEC958 in the lower left corner. 

Any ideas?

$lsmod 

> Module                  Size  Used by
nls_utf8                1568  0 
hfsplus                73632  0 
binfmt_misc             8356  1 
snd_hda_codec_nvhdmi     5084  1 
snd_hda_codec_via      53244  0 
arc4                    1660  2 
ecb                     2524  2 
snd_hda_intel          27328  0 
snd_hda_codec          84096  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               7392  1 snd_hda_codec
snd_pcm_oss            37472  0 
snd_mixer_oss          16220  1 snd_pcm_oss
snd_pcm                75424  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2752  0 
snd_seq_oss            29216  0 
ath5k                 124580  0 
mac80211              181108  1 ath5k
led_class               4096  1 ath5k
ath                     8060  1 ath5k
snd_seq_midi            6656  0 
snd_rawmidi            22336  1 snd_seq_midi
snd_seq_midi_event      7036  2 snd_seq_oss,snd_seq_midi
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd_seq                50896  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lirc_atiusb            16348  1 
lirc_dev               10804  3 lirc_atiusb
psmouse                56500  0 
cfg80211               93052  3 ath5k,mac80211,ath
serio_raw               5280  0 
ppdev                   6688  0 
x_tables               16544  1 ip_tables
parport_pc             32228  1 
asus_atk0110            8252  0 
snd_timer              21540  2 snd_pcm,snd_seq
snd_seq_device          7208  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                  4188  0 
joydev                 10240  0 
nvidia               8882020  29 
agpgart                35020  1 nvidia
snd                    60868  14 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9220  2 snd_hda_intel,snd_pcm
i2c_nforce2             6880  0 
lp                      8964  0 
parport                35340  3 ppdev,parport_pc,lp
usb_storage            52640  0 
usbhid                 38304  0 
video                  19380  0 
output                  2780  1 video
floppy                 54980  0 
forcedeth              54472  0 


[IMG]http://symbionmedia.com/alsa.png[/IMG]

---

