---
title: "No sound with Pulseaudio activated on karmic"
date: 2009-09-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ahbart on 2009-09-11
Hi,
I have problems on my new karmic installation. It is still a bit buggy in my opinion. I can live with that for a short time. But there is one thing I have serious problems with. And that's sound.

Pulseaudio is installed by default. With that I have no sound at all. All switches (mute), volume levels, are set. But there is no sound comming from the speakers. I know it is not an alsa problem, because when I remove pulseaudio from synaptic, sound is working fine. 

I've set pulseaudio to Analog Stereo Duplex. That should work. But I tried the other options too.

lspci:
```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
```

alsamixer:
```
Card: HDA Intel Chip: Realtek ALC882
```

aplay -l:
```
kaart 0: Intel [HDA Intel], apparaat 0: ALC882 Analog [ALC882 Analog]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
kaart 0: Intel [HDA Intel], apparaat 1: ALC882 Digital [ALC882 Digital]
  Sub-apparaten: 1/1
  Sub-apparaat #0: subdevice #0
```

Can someone help me here?

---

### Post by ahbart on 2009-09-11
Damn! Those developers are much too quick! ;-) 
I could not manage to use sound with pulseaudio for days. And just after I had started above thread, I updated and rebooted. And now Ubuntu plays its starting sound. 
Even skype and other applications are using pulseaudio now.
Very, very good!
I love Linux/Ubuntu and his community!

---

### Post by ECPCLINUX on 2009-09-11
Oh wow, nice to hear that. I use Skype a lot and is a pain to use since Pulse Audio. You've given me hope. :guitar:

---

### Post by ahbart on 2009-09-11
You should know that I use skype 2.1 from the skype website now. I'm not sure of skype in the medibuntu repository ispulseaudio capable.
Bart

---

