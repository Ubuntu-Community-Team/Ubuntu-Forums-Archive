---
title: "No HDMI sound output device after upgrading 20.04"
date: 2020-10-01
forum: Installation &amp; Upgrades
---

### Post by cmhrx on 2020-10-01
After upgrading from 18.04 to 20.04 I can't see HDMI audio as a choice on the sound settings.
Sound settings look like this: 

[ATTACH=CONFIG]287107[/ATTACH]


 I can hear sound by running this:

 
```
aplay -D plughw:0,3 /usr/share/sounds/alsa/Noise.wav
```


 However there is no option for HDMI. There used to be a  "Oland/Hainan/Cape Verde/Pitcairn HDMI Audio [Radeon HD 7000 Series]"  option for HDMI output in 18.04

---

### Post by slickymaster on 2020-10-01
Thread moved to **Installation & Upgrades** for a better fit

---

### Post by cmhrx on 2020-10-03
Anyone knows how to fix it?

---

### Post by AR_Kozz on 2020-10-03
I have the exact opposite problem - 20.04 upgrade lost headphones and kept HDMI, which I don't use. I can get it back by 

$sudo alsa force-reload

which might work for you too. But I don't know how to make it work right the first time it loads.

---

### Post by cmhrx on 2020-10-04
Thank you for your reply but unfortunately running that command doesn't change anything.

---

### Post by CelticWarrior on 2020-10-04
hdmi audio is at the graphics card/chip. Please post the hardware specifications.

---

