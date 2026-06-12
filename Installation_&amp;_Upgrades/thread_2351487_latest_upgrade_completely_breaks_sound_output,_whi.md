---
title: "latest upgrade completely breaks sound output, which worked perfectly before upgrade"
date: 2017-02-03
forum: Installation &amp; Upgrades
---

### Post by davidhodges.nz2 on 2017-02-03
I rebooted today for the first time in over a week and one of the updates Ubuntu installed during that time broke the sound, effective once I rebooted.
The sound still works fine if I reboot to Windoze. I've tried rebooting using older kernel versions - 4.2.0 and 4.4.57 - but neither helps. I still get no sound output at all under Linux.
The Ubuntu sound troubleshooting wiki page didn't tell me how to determine what sound card Linux thinks I have but cat /proc/asound/oss/devices 
produces no output and grepping for sound or audio in dmesg output only turns up the following:

[    7.115635] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC3234: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker[    7.115641] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)

[    7.115644] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)

[    7.115647] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0



I am running Ubuntu 16.0.4.1 LTS on a Dell Inspiron 17 5000 series.

Thanks for any help.

---

### Post by howefield on 2017-02-04
> **davidhodges.nz2 said:**
> The Ubuntu sound troubleshooting wiki page didn't tell me how to determine what sound card Linux thinks I have 

Just starting the same process with a troublesome laptop

```
sudo aplay -l
```

should give you the card.

---

### Post by davidhodges.nz2 on 2017-02-04
Thanks for that.

**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC3234 Analog [ALC3234 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

