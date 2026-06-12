---
title: "Lost sound 5.1 after upgrade to ubuntu 9.10"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by n0dix on 2009-11-22
Hi guys!!!

I had configured and installed my 5.1 sound on ubuntu 9.04 but after update it only have a 3.1.

My aplay -l:
```
**** Lista de PLAYBACK Dispositivos Hardware ****
tarjeta 0: CA0106 [CA0106], dispositivo 0: ca0106 [CA0106]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 1: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 2: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 0: CA0106 [CA0106], dispositivo 3: ca0106 [CA0106]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
tarjeta 1: NVidia [HDA NVidia], dispositivo 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdispositivos: 1/1
  Subdispositivo #0: subdevice #0
```

I have seen many threads that talk about the problem but still do not work as expected.

My .asoundrc is:
```
pcm.ca0106 {
type hw
card 0
}

ctl.ca0106 {
type hw
card 0
}

pcm.!default { #Reproducción 5.1
slave.pcm surround51
slave.channels 6
type route
ttable.0.0 1
ttable.1.1 1
ttable.0.2 1
ttable.1.3 1
ttable.0.4 0.5
ttable.1.4 0.5
ttable.0.5 0.5
ttable.1.5 0.5
}
```


Someone with any idea?

---

