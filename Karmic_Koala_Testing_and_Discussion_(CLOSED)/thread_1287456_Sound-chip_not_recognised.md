---
title: "Sound-chip not recognised"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Yumi on 2009-10-10
I have no sound in Karmic. Followed different threads to no avail. Problems I obeserve

**Puls-Audio Device Chooser** crashes with no Error message

**Gnome-Alsamixer** chrashes with the following message:
```
(gnome-alsamixer:22595): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

```

**Puls-Audio Volumne Control** in "Configuration" tells me there is "No cards available for configuration@

**cat /proc/asound/card0/codec#* | grep CodecCodec:** results in "Analog Devices AD1986A"

**aplay -l** aplay: device_list:223: no soundcards found...

My device is a onboard chip, used to work with jaunty eventually. No frilly bits, just a basic system with a speaker plugged in and use of earphones/microphone for skype required. 

Any suggestions?

Michael

---

