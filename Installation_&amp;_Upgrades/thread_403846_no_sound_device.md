---
title: "no sound device"
date: 2007-04-07
forum: Installation &amp; Upgrades
---

### Post by gunghoiguana on 2007-04-07
I just installed Edgy Eft on a machine with a P5LD2 mainboard, which has sound built in.  It's saying there are no sound devices.  The good news is that lspci finds it:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: ASUSTeK Computer Inc. Unknown device 8237
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at cdcf8000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

Sure enough, it's there in /dev/snd, and asoundconf sees it:

$ls /dev/snd
controlC0  pcmC0D0c  pcmC0D0p  pcmC0D1p  pcmC0D2c  timer

$asoundconf list
Names of available sound cards:
Intel

But when I run alsactl, it doesn't see it, even though asound.names looks ok.

$ alsactl names
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 0 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 1 failed: No such device
alsactl: for_each_card:51: No soundcards found...
alsactl: generate_names:525: probe 2 failed: No such device
alsactl: generate_names:525: probe 3 failed: Permission denied
alsactl: generate_names:538: Cannot open /etc/asound.names for writing

This feels like it's just a simple misconfiguration--something doesn't have the right location for the sound card or some such.  I just don't know enough about ubuntu or alsa to know where to look.  Any ideas?

Thanks!

---

