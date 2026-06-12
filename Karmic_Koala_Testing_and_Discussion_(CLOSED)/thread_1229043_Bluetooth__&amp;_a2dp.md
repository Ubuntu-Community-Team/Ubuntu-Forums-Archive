---
title: "Bluetooth  &amp; a2dp"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by martijntje on 2009-08-01
I have a Jabra BT3030 bluetooth headset. While ubuntu correctly recognizes it and a sync appears, the audio quality is simpy awful.

This is probably because the computer is not using the a2dp profile for music playback. Is it possible to use a2dp here? And so, how? I know I can add it to the asoundrc file, but i'd rather have a way to configure the pulseaudio bluetooth module.

---

### Post by KhaaL on 2009-08-02
this issue has been a thorn in my side for as long as i remember. I was recommended to use [http://blueman-project.org/](http://blueman-project.org/) but I don't remember it helping me much. If you manage to solve this, please let us know how.

---

### Post by martijntje on 2009-08-02
Well, I "solved" it, and boy was it easy! :D

Turns out, if you open pavucontrol (Pulseaudio Volume Control) and go to the configurations tab, you can select a profile. It's set to Telephone Duplex by default, but you can change it to HFP there.

---

