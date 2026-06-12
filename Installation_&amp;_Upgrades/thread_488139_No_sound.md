---
title: "No sound"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by Mike7171 on 2007-06-29
I am brand new to Ubuntu, and a few minutes ago I tried to enable the Desktop Effects. I have an NVIDIA Graphics card, and it told me I needed NVIDIA Advanced Graphics something. Anyway, I chose "Ok" and it installed/upgraded it. I rebooted, and the desktop effects sort of worked, but Ubuntu told me that it may not work properly because the new graphics card thing isn't supported.  Now, I have no sound. I think everything works fine except sound. I have no idea how to undo the upgrade (if possible) and I don't know how to get my sound back. Any ideas?

Thanks,
Mike7171

---

### Post by phizikal on 2007-06-29
Yeah, im not getting sound either. It says something about i dont have gstreamer pluggins, but i dont know which ones to get.

---

### Post by Mike7171 on 2007-06-29
Did you do the same thing as me to cause it?

And does anyone know how to fix this?

---

### Post by Mike7171 on 2007-06-29
Not sure if it helps, but the output to "aplay -l" is

```
**** List of PLAYBACK Hardware Devices ****
card 0: rev50 [VIA 82C686A/B rev50], device 0: VIA 82C686A/B rev50 [VIA 82C686A/B rev50]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Live [SBLive 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 1: Live [SBLive 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 1: Live [SBLive 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I also double-clicked the speaker in the top right corner of my screen, and it was not muted.

---

### Post by firedancer on 2007-06-29
undo desktop effects 
system>>preferences>>desktop effects 


i don't have another alternative but you can try reboot, 

sometimes alsa freaks (in my situation)


not an expert , passing by .....:)



phizikal get all gstreamer plugins.....worked for me ........>synaptic

---

### Post by Mike7171 on 2007-06-29
I already turned off Desktop Effects. Still no sound. Thank you for trying though.

---

### Post by senken12 on 2007-06-30
I have the exact same problem... But I don't think it was when I attempted to use the NVIDIA thing... It seemed to happen after I upgraded to Feisty Fawn (Although I didn't try using my sound before I attempted...)

---

### Post by Mike7171 on 2007-06-30
I haven''t tried upgrading Feisty Fawn yet, so I do not know if it will do the same to me. The NVIDIA thing did though. No sites seem to have anything about it either.

---

