---
title: "no sound on ubuntu 15.04"
date: 2015-08-15
forum: Installation &amp; Upgrades
---

### Post by Stphane_Delanoue on 2015-08-15
Hi
for some time now I try to get audio working on ubuntu 15.04 with no success

not the audio works fine on linux mint widows 7 and Windows 10

after install ubuntu_desktop from server edition 15.04 I get no sound
the reason I started with server edition is that the desktop install do not boot due to a wrong driver for my 8880 GTX board

I installed ubuntu server 15.04 x64 and then:
 ubuntu_desktop
 nvidia_340

alsa see my card as well as NVIDIA HDMI output (not plugged)

but pulseaudio only show the NVidia HDMI

I tried to uninstall and resinstall pulseaudio

HDMI has gone but still not see my intel board only get dummy ouput

now alsa see correctly the card but still not pulse

all alsa information on system can be found here :
[http://www.alsa-project.org/db/?f=fa97f985d8a7fe9709dc001406b544b236e92c6a](http://www.alsa-project.org/db/?f=fa97f985d8a7fe9709dc001406b544b236e92c6a)

aplay -l
**** Liste des Périphériques Matériels PLAYBACK ****
carte 0: MID [HDA Intel MID], périphérique 0: VT2020 Analog [VT2020 Analog]
  Sous-périphériques: 0/1
  Sous-périphérique #0: subdevice #0
carte 0: MID [HDA Intel MID], périphérique 2: VT2020 Alt Analog [VT2020 Alt Analog]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0
carte 0: MID [HDA Intel MID], périphérique 3: VT2020 Digital [VT2020 Digital]
  Sous-périphériques: 1/1
  Sous-périphérique #0: subdevice #0

lspci -nn | grep '\[04[80][13]\]'
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 06)

lspci -ks 00:1b.0 
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
    Subsystem: ASUSTeK Computer Inc. Device 8375
    Kernel driver in use: snd_hda_intel

lsmod | grep hda_intel
snd_hda_intel          36864  5 
snd_hda_controller     32768  1 snd_hda_intel
snd_hda_codec         143360  4 snd_hda_codec_via,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
snd_pcm               106496  6 snd_usb_audio,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd                    90112  27 snd_usb_audio,snd_hwdep,snd_timer,snd_hda_codec_via,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_usbmidi_lib,snd_hda_codec,snd_hda_intel,snd_seq_device


thans for your help
regards,
Stephane

---

### Post by dino99 on 2015-08-15
recently i also hit that issue on my system which was getting sound without issue. I made no hardware config change, but suddenly (after some upgrades) i stopped getting sound output.
This was due to pulseaudio now used which is very sensitive: it needs 'hda' set into the bios/uefi (not ac97 as i was having) and the jack(s) also needs be be stricly plugged as they might (same color plugged together)
Its a good idea to have pref & pavucontrol to finally tune your sound prefs

---

