---
title: "Sound issues after upgrading"
date: 2020-03-25
forum: Installation &amp; Upgrades
---

### Post by aviroop123 on 2020-03-25
I recently upgraded my ubuntu to ubuntu 5.3.0-42. After the update, there were sound problems associated. Automatically sometimes the sound goes off after restart or after log out. Once when I connected my headphones, the left speaker of the headphone and the right speaker of the laptop were working simultaneously. Also, I am not able to adjust the volume of sound by any means. I have followed on many links to fix this problem, but none have worked. When I log in through 5.3.0-42 generic, dummy output is shown in the sound settings, but when I log in through 5.3.0-40, boht the speakers are detected but the same problem arises.

I have tried changing the settings in alsamixer and force-reload, but then the sound goes off completely.

Note: The sound works fine in windows 10.

Any help would be appreciated. Thanks!

---

### Post by MimziM on 2020-03-26
Have you tried purging and reinstalling alsa 

```
sudo apt-get remove --purge alsa-base pulseaudio
```
```
sudo apt-get install alsa-base pulseaudio
```
```
sudo alsa force-reload
```

---

