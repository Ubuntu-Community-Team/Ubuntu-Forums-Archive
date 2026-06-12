---
title: "No sound"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Sandsound on 2009-10-13
I have had a lot of problems with Karmic and sound the last few days, most of them trivial and easy to fix, but the latest updates have forced me to reinstall Karmic in the hope that this would solve my problems.

Pulse still doesn't give me an option to choose analog i/o, and I have to fix it by manually editing the /lib/udev/rules.d/90-pulseaudio.rules file like suggested here : [http://ubuntuforums.org/showthread.php?t=1268856&highlight=ice1712]("http://ubuntuforums.org/showthread.php?t=1268856&highlight=ice1712")

Unfortunately this doesn't do it alone, I also have to turn up the volume in alsamixer, and heres where it gets tricky... it won't remember my settings ???

I have tried running :
```
sudo alsactl store 0
```
but it still doesn't remember my settings.

btw. my sound-card is a M-Audio Audiophile 2496 (ice1712)

---

### Post by johoe on 2009-10-13
same problems here. It seems that alsactl is not run at startup/shutdown. When I run a "sudo alsactl restore" all my settings are restored I saved before...

johoe

---

### Post by Sandsound on 2009-10-13
> **johoe said:**
> same problems here. It seems that alsactl is not run at startup/shutdown. When I run a "sudo alsactl restore" all my settings are restored I saved before...

johoe

I made a "alsactl restore" entry in my "startup applications" and that did the trick, works without sudo btw.

So thanks for pointing me in the right direction :-)

---

### Post by johoe on 2009-10-13
fine - hope we'll soon reach jaunty's level - pulse and m2496 there is a perfect team...
I am missing the "rerouting" sound streams feature - so I can route skype's output to the internal intel card with headphone.

  johoe

---

### Post by waspbr on 2009-10-13
the "fix" seemed to work, though the latest updates broke it again on my hp tx1320us. All I am left with is a dummy output and internal audio is not listed in PA. 

A step in the right direction but there is something else missing. Sound hasn't worked for me since alpha 4, I have already filed a bug report but this is the first time I got somewhere, well back to the usb audio adapter for me.

---

### Post by Sandsound on 2009-10-13
> **johoe said:**
> ..pulse and m2496 there is a perfect team...

you are kidding right ? :shock:

Once I'm done testing Karmic, Pulse is the first thing I'll remove :-)

I was very exited when I first heard about Pulse, but I have never had it working like I want.
Alsa may require some tweaking, but once it's working, it's stable.
Also... wineasio is a must for me, and it doesn't work with pulse.

---

### Post by johoe on 2009-10-14
aehm, no not kidding. I really had no problems in Jaunty.
to my opinion the sound quality is generally poor in linux (gstreamer-pulse). to me xine-alsa is a better combination. 
But I never reached same sound quality from windows. so I boot windows from time to time...

---

