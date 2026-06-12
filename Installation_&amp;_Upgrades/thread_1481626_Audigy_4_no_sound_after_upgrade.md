---
title: "Audigy 4 no sound after upgrade"
date: 2010-05-12
forum: Installation &amp; Upgrades
---

### Post by the_overmaster on 2010-05-12
Sound does not work in my newly installed 10.04 (why I upgraded I will never know - I'm back to the same slowness problems with my ATI Radeon card as well).  This time, however, I seemingly can't use my previous lazy approach of just switching on Digital support - it still won't work.  Any suggestions - I'm really bad with Linux - and I have tried a couple of suggestions (I haven't recompiled alsa) - none of it will work.

Below is the output from an aplay -l command...

Thanks in advance if anyone can get me out of this mess - I gots to have my music - I might as well be using Windows if I have no music.

> **** List of PLAYBACK Hardware Devices ****
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Audigy2 [SB Audigy 4 [SB0610]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by kostkon on 2010-05-12
Did you try to setup your card again in System &#8594; Preferences &#8594; Sound?

Also, install gnome-alsamixer and check your hardware volume levels and especially make sure that the *Digital/Analog* switch is not enabled.

---

### Post by the_overmaster on 2010-05-12
yes - have tried all the quick - easy fixes, I have even reinstalled alsamixer and everything (again, not recompiled) - still nothing.  I got BS on 10.04.. anyone have any technical suggestions that they are ready and willing to spell out clearly (as I haven't been Linuxing very long)?

---

### Post by raygj on 2010-05-13
> **the_overmaster said:**
> yes - have tried all the quick - easy fixes, I have even reinstalled alsamixer and everything (again, not recompiled) - still nothing.  I got BS on 10.04.. anyone have any technical suggestions that they are ready and willing to spell out clearly (as I haven't been Linuxing very long)?

give this a go
[http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script]("http://ubuntuforums.org/showthread.php?t=1046137&highlight=alsa+upgrade+script")

---

