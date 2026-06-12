---
title: "Music codecs?"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by foolish one on 2008-03-26
Which packages should I install if I want to be able to play all of my music. (mp3, wma, wav, ogg, m4a, m4p. etc.)

---

### Post by Pumalite on 2008-03-26
sudo aptitude install ubuntu-restricted-extras

---

### Post by stchman on 2008-03-26
> **foolish one said:**
> Which packages should I install if I want to be able to play all of my music. (mp3, wma, wav, ogg, m4a, m4p. etc.)

This will get them all.

```


sudo apt-get -y install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse
```

---

### Post by Pumalite on 2008-03-26
Make Medibuntu a part of your /etc/apt/sources.list and install all the codecs you need:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by foolish one on 2008-03-27
thanks guys. that 's all I needed.

---

### Post by Club17 on 2008-04-19
Thank you to all, solved for me, too.

---

