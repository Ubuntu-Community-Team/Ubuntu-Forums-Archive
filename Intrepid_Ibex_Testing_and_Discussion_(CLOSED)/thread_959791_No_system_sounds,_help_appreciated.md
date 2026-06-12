---
title: "No system sounds, help appreciated"
date: 2008-10-26
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by mdurham on 2008-10-26
All other sound is okay, I just have no system sound on either 32 or 64 bit Ubuntu.
Also, aplay shows that I have two sound devices on my motherboard. Is that normal?

Cheers, Mike

> mike@intrepid_on7:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


---

### Post by tuxxy on 2008-10-26
Can you hear the system sounds located in the sound prefs?

---

### Post by mdurham on 2008-10-26
> **tuxxy said:**
> Can you hear the system sounds located in the sound prefs?

Yes, I can click on 'Button clicked' or 'Alert sound' etc... and hear the sound.

---

### Post by FuturePilot on 2008-10-26
Same problem here. It's a bug.
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")

---

### Post by mdurham on 2008-10-26
> **FuturePilot said:**
> Same problem here. It's a bug.
[https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507]("https://bugs.launchpad.net/ubuntu/+source/libcanberra/+bug/273507")

Thanks FuturePilot, that fixed it.

---

