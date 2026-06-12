---
title: "how to install codecs without automatix (it does not have them anymore)?"
date: 2006-10-30
forum: Installation &amp; Upgrades
---

### Post by 1002285 on 2006-10-30
I got this piece of advice
"Please go to [http://www4.mplayerhq.hu/MPlayer/releases/codecs/](http://www4.mplayerhq.hu/MPlayer/releases/codecs/) and download (save to disk) all-20060611.tar.bz2"
in my earlier thread.
(I could not install multimedia codecs, because automatix does not have them anymore).

I downloaded the pack, but what do I do next? How to install them?

---

### Post by gborzi on 2006-10-30
You can get these codecs and other packages from seveas's repository, look here: [http://mirror.ubuntulinux.nl/]("http://mirror.ubuntulinux.nl/")

Regards.

---

### Post by Kateikyoushi on 2006-10-30
Aren't these the w32 codecs ? I installed every codec I found in synaptic on multiverse and universe and now can play everything.

This should install the w32codecs.
```
sudo aptitude install w32codecs
```

---

### Post by scotty32 on 2006-10-30
ive got Edgy, and i just installed Amarok, and it said "amarok cannot play mp3's would you like to install them now?"

clicked yes, and it asked me to restart amarok - now i can play mp3s

but make sure that the package manager loads up (and/or asks for a password) otherwise it lied, and it didnt install the codecs, just keep playin the song till it loads the package manager - as it does **not** do a 'silent' install (so much wasted time restartin amarok ](*,) )

---

### Post by 1002285 on 2006-10-30
> **Kateikyoushi said:**
> Aren't these the w32 codecs ? I installed every codec I found in synaptic on multiverse and universe and now can play everything.

This should install the w32codecs.
```
sudo aptitude install w32codecs
```

Thanks for trying, but it does not seem to be that simple. I did install w32codecs and avi files are not playing.

---

### Post by larytet on 2006-11-07
same here
win32 installed and i have sound, not video 
Ubuntu 6.10 - the Edgy Eft
I tried AVI files. I think I did all usual tricks including download of all-20060611.tar.bz2  from MPLayer web site and putting them to /usr/local/lib/codecs/ I did  sudo apt-get install gstreamer0.10-ffmpeg gstreamer0.10-gl gstreamer0.10-plugins-base gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine-extracodecs w32codecs
and so on
Nothing

---

