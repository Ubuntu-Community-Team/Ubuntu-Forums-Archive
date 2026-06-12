---
title: "No sound a while after pulseaudio -k"
date: 2009-04-21
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by barisurum on 2009-04-21
Hi,

My card is a usb-audio device:

```
**** List of PLAYBACK Hardware Devices ****
card 1: XStation [XStation], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

I have no login sound after boot and in sys/pref/sound test sound doesn't work. But when I do:

```
pulseaudio -k
```

I have sound for a while but then pulseaudio segfaults and all goes silent. Dmesg reports pulseaudio blabla segfault at blabla error 14 etc.

when I:

```
pulseaudio X11
```

I get an error:

```
E: alsa-util.c: Error opening PCM device hw:1: Device or resource busy
E: module.c: Failed to load  module "module-alsa-source" (argument: "device_id=1 source_name=alsa_input.usb_device_1235_6_noserial_if0_sound_card_0_alsa_capture_0 tsched=0"): initialization failed.
```

and after a while a series of errors:

```
E: module-alsa-sink.c: Failed to set hardware parameters: Operation not permitted
```

going on and on

What could be the cause and is there a fix for this? Thank you.

---

### Post by barisurum on 2009-04-22
any ideas?

---

