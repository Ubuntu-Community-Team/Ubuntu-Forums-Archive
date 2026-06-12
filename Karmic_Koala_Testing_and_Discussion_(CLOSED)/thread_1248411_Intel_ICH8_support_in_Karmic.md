---
title: "Intel ICH8 support in Karmic?"
date: 2009-08-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by simmeson on 2009-08-24
Hi!

On my Sony Vaio VGN-AR61M I have an audio card which belongs to ICH8 family. That card is giving me serious problems in Jaunty. I get sound, but headphones or speakers doesnt work when plugged. I also have problems with low volume. I wonder if there's better support for it in Karmic? Karmic are using a newer kernel that the one Jaunty currently use(2.6.28-15), so it should have better support?

This card is what I have:
```
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
```

---

### Post by taavikko on 2009-08-24
Post the results of
```
aplay -l
grep -i codec /proc/asound/card0/codec#0
```
Which will tell lot more.

Please also check if the headphone's is muted via 
```
alsamixer
alsamixer -Dhw
```

---

### Post by simmeson on 2009-08-24
> **taavikko said:**
> Post the results of
```
aplay -l
grep -i codec /proc/asound/card0/codec#0
```
Which will tell lot more.

Please also check if the headphone's is muted via 
```
alsamixer
alsamixer -Dhw
```

Allright, here they are.

```
simon@Rieju:~$ aplay -l
**** Lista över PLAYBACK hårdvaruenheter ****
kort 0: Intel [HDA Intel], enhet 0: STAC92xx Analog [STAC92xx Analog]
  Underordnade enheter: 0/1
  Underordnad enhet nr. 0: subdevice #0
kort 0: Intel [HDA Intel], enhet 2: ALC262 Analog [ALC262 Analog]
  Underordnade enheter: 1/1
  Underordnad enhet nr. 0: subdevice #0
```

```
simon@Rieju:~$ grep -i codec /proc/asound/card0/codec#0
Codec: SigmaTel CXD9872AKD
```

My sound problems are already solved, I compiled alsa myself to get it working. My question is just if I still have to recompile alsa every time i reinstall even in Karmic? :)

---

