---
title: "No sound on EeePC 1015PX internal speakers, only on Ubuntu"
date: 2017-04-19
forum: Installation &amp; Upgrades
---

### Post by timothylegg on 2017-04-19
I recently deployed a used netbook into my fleet of Linux machines.  It is the first one of these to have a modern version of Ubuntu (16.04 LTS)

There was no sound.  I figured no big deal, I've dealt with things before...

From 'System Settings' -> 'Sound' and with 'Play sound through' set to "Speakers", I go to 'Test Sound', but only get silence.

I attach an external speaker,

From 'System Settings' -> 'Sound' and with 'Play sound through' set to "Headphones", I go to 'Test Sound', and now it works.

The internal speakers are functional and I have verified them to operate an a competing operating system.

I followed the steps on:

[https://help.ubuntu.com/16.04/ubuntu-help/sound-nosound.html](https://help.ubuntu.com/16.04/ubuntu-help/sound-nosound.html)

And I found nothing out of the ordinary from aplay or lspci.  Everything seems to be in order...

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC269VB Analog [ALC269VB Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


$ sudo lspci -v


00:1b.0 Audio device: Intel Corporation NM10/ICH7 Family High Definition Audio Controller (rev 02)
    Subsystem: ASUSTeK Computer Inc. NM10/ICH7 Family High Definition Audio Controller
    Flags: bus master, fast devsel, latency 0, IRQ 29
    Memory at f7cf8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


What did I miss?

Tim

---

