---
title: "[SOLVED] No sound on HP 8530w"
date: 2008-10-25
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by falstaff on 2008-10-25
Hello,

I have no sound on my HP EliteBook 8530w. Sound works through headphone jack, but not the built-in speaker. I thought always this is just a hardware switch (when jack is plugged, speaker goes of and visa versa)

aplay -l shows this...
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Any idea? How can I debug this further?

bye
falstaff

---

### Post by falstaff on 2008-10-25
I opened a bug report at alsa-project.org for this...

[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4199]("https://bugtrack.alsa-project.org/alsa-bug/view.php?id=4199")

---

### Post by mweyland2 on 2008-10-25
Hello

Try loading snd-hda-intel with the option model=laptop

Helped on my 8530p

Please let me know if this works for you as well to help to report to upstream as accurate as possible.

Regards

Matt

---

### Post by falstaff on 2008-10-26
Hello,

Yess! It works!

For the records:
```

$ sudo vi /etc/modprobe.d/alsa-base

```
And at this at the end of the file:
```

options snd-hda-intel model=laptop

```

Does the volume keys on the laptop works for you? For me they doesnt. Mute works, but Volume up/down doesnt works... Any idea?

And another Question: Does ACPI works on your laptop?

bye
falstaff

---

