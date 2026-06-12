---
title: "last kernel update 6.5.0-15 ubuntu 22.04 make pulseeffects not to detec source sounds"
date: 2024-01-28
forum: Installation &amp; Upgrades
---

### Post by jiriky on 2024-01-28
Greetings from Spain,(sorry for my english, i have long forgotten it)  a few days ago i have instaled the last update (kernel 6.5.0-15 and mesa drivers) all seems ok, but then when this morning i have try to hear music, pulse effects not detect any sorce of sounds. I have tried instaling easy effects, nothing changed, I have restored with timeshift ( a backup made  before the kernel update) and pulseeffects works again. Of course, purge and autoremove and reinstall don't work either. Some suggestion??
OS: Ubuntu 22.04.3 LTS x86_64 
    Host: 80Y8 Lenovo YOGA 920-13IKB Gla 
    Kernel: 6.5.0-15-generic 
    Packages: 3321 (dpkg), 17 (snap) 
   Shell: bash 5.1.16 
   Resolution: 2048x1152 
  DE: GNOME 42.9 
  CPU: Intel i7-8550U (8) @ 4.000GHz 
  GPU: Intel UHD Graphics 620 
  Memory: 4861MiB / 15730MiB 
lsmod | grep snd_hda_intel
snd_hda_intel          61440  3
snd_intel_dspcfg       32768  5 snd_soc_avs,snd_hda_intel,snd_sof,snd_sof_intel_hda_common,snd_soc_skl
snd_hda_codec         212992  9 snd_hda_codec_generic,snd_soc_avs,snd_hda_codec_hdmi,snd_soc_hda_codec,snd_hda_intel,snd_hda_codec_realtek,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_hda_core          147456  12 snd_hda_codec_generic,snd_soc_avs,snd_hda_codec_hdmi,snd_soc_hda_codec,snd_hda_intel,snd_hda_ext_core,snd_hda_codec,snd_hda_codec_realtek,snd_sof_intel_hda_common,snd_soc_hdac_hda,snd_soc_skl,snd_sof_intel_hda
snd_pcm               196608  13 snd_soc_avs,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,soundwire_intel,snd_sof,snd_sof_intel_hda_common,snd_compress,snd_soc_core,snd_sof_utils,snd_soc_skl,snd_hda_core,snd_pcm_dmaengine
snd                   143360  20 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_hda_codec_realtek,snd_sof,snd_timer,snd_compress,snd_soc_core,snd_pcm,snd_rawmidi

---

### Post by MAFoElffen on 2024-01-30
I found a report that said that many recent Lenovo were having problems with audio similar to your were there was a patch applied in the kernels, but also required option set for those modules...
RE: [https://discussion.fedoraproject.org/t/problem-with-sound-on-new-lenovo-laptops/72456/4](https://discussion.fedoraproject.org/t/problem-with-sound-on-new-lenovo-laptops/72456/4)

To see if those modules are loaded:
```

lsmod | grep 'snd_intel_dspcfg\|snd_hda_intel'

```
Then add the options to file /etc/modprobe.d/alsa-base.conf:
```

sudo echo "options snd_intel_dspcfg dsp_driver=1" >> /etc/modprobe.d/alsa-base.conf
sudo echo "options snd_hda_intel model=alc287-yoga9-bass-spk-pin" >> /etc/modprobe.d/alsa-base.conf
sudo reboot

```

---

### Post by jiriky on 2024-02-01
Thanks so much, i'm going to give a try, i 'll tell about adding the modules
After de try (the modules are loaded) pulseeffects is not working yet.

---

