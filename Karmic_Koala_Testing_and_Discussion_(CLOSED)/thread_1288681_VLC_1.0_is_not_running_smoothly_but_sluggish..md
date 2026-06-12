---
title: "VLC 1.0 is not running smoothly but sluggish."
date: 2009-10-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by donniezazen on 2009-10-11
Greetings,

As the title says for some reason VLC 1.0 is not running smoothly. The video is fine but the sound is interrupted. I have a dell 6400/E1505.

Please help,
SK

---

### Post by GoldNugget on 2009-10-11
I have noticed the same problem on my EEE PC 900 with VLC and Flash videos. Oddly, it plays fine the first time, but if I pause, restart or otherwise interrupt it, the audio begins skipping every few seconds. I had figured this was related to the performance regression in Intel video in the last few updates and was hoping for a fix before the final release.

---

### Post by donniezazen on 2009-10-11
> **GoldNugget said:**
> I have noticed the same problem on my EEE PC 900 with VLC and Flash videos. Oddly, it plays fine the first time, but if I pause, restart or otherwise interrupt it, the audio begins skipping every few seconds. I had figured this was related to the performance regression in Intel video in the last few updates and was hoping for a fix before the final release.

This problem is only with VLC 1.0 but not in Totem. Though Intel graphic card is also in problem. I am not able to enable desktop effect. We are few days from final release and Ubuntu is gripped in this major problem.

---

### Post by TrueTom on 2009-10-11
```
sudo apt-get install vlc-plugin-pulse
```

Then change the output plugin in the VLC settings...

---

### Post by donniezazen on 2009-10-11
> **TrueTom said:**
> ```
sudo apt-get install vlc-plugin-pulse
```

Then change the output plugin in the VLC settings...

What does this means.

vlc-plugin-pulse is already the newest version.
vlc-plugin-pulse set to manually installed.

---

### Post by hexion on 2009-10-11
> **TrueTom said:**
> ```
sudo apt-get install vlc-plugin-pulse
```Then change the output plugin in the VLC settings...

I have the same problem as reported in this thread and I had my VLC already configured with pulseaudio as the sound output plugin so unfortunately that's not the solution.

---

### Post by froggyswamp on 2009-10-11
Same here.
Pretty bad.
I've been waiting for Karmic to get rid of the VLC issue from Jaunty which always opened a second (video) window and was annoying. The new version in Karmic fixed that but introduced the sound issue. Totem lacks too many basic features to be considered as a good alternative.

---

### Post by donniezazen on 2009-10-11
> **froggyswamp said:**
> same here.
Pretty bad.
I've been waiting for karmic to get rid of the vlc issue from jaunty which always opened a second (video) window and was annoying. The new version in karmic fixed that but introduced the sound issue. Totem lacks too many basic features to be considered as a good alternative.

+1

---

### Post by muximus on 2009-10-12
+1

but surprisingly, totem works fine..

---

