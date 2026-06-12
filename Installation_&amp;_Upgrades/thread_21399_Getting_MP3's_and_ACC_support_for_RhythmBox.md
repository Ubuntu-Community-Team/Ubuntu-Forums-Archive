---
title: "Getting MP3's and ACC support for RhythmBox"
date: 2005-03-22
forum: Installation &amp; Upgrades
---

### Post by Insanely on 2005-03-22
Hello,

I quite like the look and functionality of rhythmbox. But... I have an ipod with mainly MP3's and AAC files (m4u i think). Is there any sort of plugin I can download or something to be able to play mp3 and aac files through rhythym box? I am using xmms at the moment. It reminds me a lot like winamp and I don't like it to much!

Thankyou for any help

uname -a
Linux hoary 2.6.10-5-386 #1 Tue Mar 15 14:43:37 UTC 2005 i686 GNU/Linux

---

### Post by Insanely on 2005-03-22
aahh found it!

[http://ubuntuguide.org/#codecs](http://ubuntuguide.org/#codecs)

I didn't realise that GStreamer plugins would install support for rhythymbox!

---

### Post by Leif on 2005-03-22
As far as I know, that will get you mp3 support, but not AAC support (yet). I've added  deb [http://luca.pca.it/debian/](http://luca.pca.it/debian/) ./ to my sources, and got gstreamer-faad. Works fine.

---

### Post by jay156 on 2005-04-30
i installed gstreamer-faad , but it got conflict with the players. Someone have any clues?

---

