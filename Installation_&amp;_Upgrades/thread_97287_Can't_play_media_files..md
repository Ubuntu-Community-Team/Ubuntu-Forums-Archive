---
title: "Can't play media files."
date: 2005-11-30
forum: Installation &amp; Upgrades
---

### Post by Demetriustyus on 2005-11-30
Hi, I'm new to linux and I can't play any mp3's or mpegs. I get error messages from the totem player.  How do i get my music and videos to play? My soundcard works because I hear music when I login. 

Also, I have an Athlon XP processor and dont know which item to click on to download programs. Some of the choices are i386, amd64, arm, alpha...etc. Which one do i click on? 

Thanks.

---

### Post by taurus on 2005-11-30
Have you tried xmms for your mp3s and mplayer for your videos???  i386 is what you want since your AMD XP is a 32bit, not 64 like AMD64...  Both are working great on my machine.

---

### Post by cowlip on 2005-11-30
I would type this into a terminal (under applications).. sudo apt-get install totem-xine gstreamer0.8-plugins gstreamer0.8-plugins-multiverse gstreamer0.8-ffmpeg and then follow this: [https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba](https://wiki.ubuntu.com/RestrictedFormats#head-fda9cc5147253891fe3047263b82d787ab025bba)

---

