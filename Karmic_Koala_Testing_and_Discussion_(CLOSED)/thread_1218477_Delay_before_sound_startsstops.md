---
title: "Delay before sound starts/stops"
date: 2009-07-20
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Craigy90 on 2009-07-20
This is an issue I've had for a while, but assumed that it was a problem with the pulseaudio transition or something.

Anyway, what happens is when I start playing a sound in any program, there is a delay of about 7 seconds before I actually start hearing the sound. I hear a *pop* then hear the sound work. When I stop playing the sound, I count around 13 seconds then I hear another *pop* when the speakers turn off again.

Does this look like a problem with pulseaudio, or something else? Any help/suggestions/advice is appreciated. Thanks! :popcorn:

---

### Post by taavikko on 2009-07-21
Devs incorporated power-save feature for hda-intel chips.
The delay is 10s, i'll suspect that this is due to that change...

To verify, just comment out (add # to beginning of the line) the last line in /etc/modprobe.d/alsa-base.conf
```
#options snd-hda-intel power_save=10
```

---

### Post by Craigy90 on 2009-07-21
Thanks a lot, that is the cause indeed. I have found a bug report for the noise when it disables/enables the chip:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

---

### Post by Craigy90 on 2009-07-21
> **Craigy90 said:**
> Thanks a lot, that is the cause indeed. I have found a bug report for the noise when it disables/enables the chip:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/381201)

Actually it seems that they want anyone who experiences pops due to the power-save option to report separate bugs. D'oh!

[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2009-May/008239.html)

---

### Post by Longinus00 on 2009-09-09
I'm getting the same thing and want to file a bug but I'm not sure how to get the hwinfo that is usually included in the bug report.

These are the files I'm wondering how to get.
    * AlsaDevices.txt  (347 bytes, text/plain; charset="utf-8")
    * BootDmesg.txt (42.5 KiB, text/plain; charset="utf-8")
    * Card0.Amixer.values.txt (1.9 KiB, text/plain; charset="utf-8")
    * Card0.Codecs.codec.0.txt (8.3 KiB, text/plain; charset="utf-8")
    * CurrentDmesg.txt (13.2 KiB, text/plain; charset="utf-8")
    * Dependencies.txt (1.2 KiB, text/plain; charset="utf-8")
    * PciMultimedia.txt (601 bytes, text/plain; charset="utf-8")

---

### Post by taavikko on 2009-09-10
> **Longinus00 said:**
> I'm getting the same thing and want to file a bug but I'm not sure how to get the hwinfo that is usually included in the bug report.

These are the files I'm wondering how to get.
    * AlsaDevices.txt  (347 bytes, text/plain; charset="utf-8")
    * BootDmesg.txt (42.5 KiB, text/plain; charset="utf-8")
    * Card0.Amixer.values.txt (1.9 KiB, text/plain; charset="utf-8")
    * Card0.Codecs.codec.0.txt (8.3 KiB, text/plain; charset="utf-8")
    * CurrentDmesg.txt (13.2 KiB, text/plain; charset="utf-8")
    * Dependencies.txt (1.2 KiB, text/plain; charset="utf-8")
    * PciMultimedia.txt (601 bytes, text/plain; charset="utf-8")

Did you read the link that Craigy provided...

Run "ubuntu-bug alsa-base"

---

