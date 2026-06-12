---
title: "Sound Problem with new 24.04"
date: 2024-10-09
forum: Installation &amp; Upgrades
---

### Post by Dirk_Ouellette on 2024-10-09
[]("https://askubuntu.com/posts/1529508/timeline")  
          
                                        I was using 22.04 until 2 days ago with my Motu M4 usb interface  working beautifully. I just installed 24,04 into a newer laptop. Sound  is awful. I will post whatever is needed to get some help?

**So far;     **aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [LEN T2454pA]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC285 Analog [ALC285 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: M4 [M4], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


ALSO;  dmesg | grep -i audio
dmesg: read kernel buffer failed: Operation not permitted
hapibeli@hapibeli-ThinkPad-P52:~$ $ sudo dmesg | grep -i audio
$: command not found
hapibeli@hapibeli-ThinkPad-P52:~$  sudo dmesg | grep -i audio
[  367.629415] snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
[  367.900992] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[  368.146607] snd_hda_codec_realtek hdaudioC1D0: autoconfig for ALC285: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[  368.146624] snd_hda_codec_realtek hdaudioC1D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[  368.146632] snd_hda_codec_realtek hdaudioC1D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[  368.146639] snd_hda_codec_realtek hdaudioC1D0:    mono: mono_out=0x0
[  368.146644] snd_hda_codec_realtek hdaudioC1D0:    inputs:
[  368.146648] snd_hda_codec_realtek hdaudioC1D0:      Mic=0x19
[  368.146654] snd_hda_codec_realtek hdaudioC1D0:      Internal Mic=0x12
[  369.087914] usbcore: registered new interface driver snd-usb-audio

---

### Post by bobunderwood99 on 2024-10-09
.

---

### Post by Dirk_Ouellette on 2024-10-11
Well, I reinstalled the 22.04 sdd on my Lenovo P52, as it worked great  on my Lenovo T440s. I then updated and upgraded the drive. Same exact  problem as the sdd with 24.04 on it, so, it's the machine. 
  The issue to be very clear, is a constant stream of noise whether I have my Motu M4 USB interface running or not.  Watching YouTube or listening to anything else, there is constant interference like noise happening.
  Where to begin?

---

