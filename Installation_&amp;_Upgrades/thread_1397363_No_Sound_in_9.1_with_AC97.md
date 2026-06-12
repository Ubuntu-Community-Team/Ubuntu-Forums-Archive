---
title: "No Sound in 9.1 with AC97"
date: 2010-02-03
forum: Installation &amp; Upgrades
---

### Post by Frozen001 on 2010-02-03
I have an older HP desktop that I recently installed ubuntu 9.10.  Currently I do not get any system sounds.  I can get sound from the movie player so I know something must be correct.  When booting I can hear the speaker pop several times, but that is it.  On my other machine with 9.10 installed I get a sound during the splash screen.

---

### Post by tommcd on 2010-02-03
Open a terminal and run **alsamixer**. If any of the levels are muted, unmute them by selecting them with the arrow keys and then toggling the 'M' key. Move all the levels up with the up arrow key. When all levels are unmuted and set at 90-100%, hit the Esc key twice to exit alsamixer.

If alsamixer does not correct the sound problem, try working your way through this troubleshooting guide:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Frozen001 on 2010-02-03
OK I have it sort of working, but it is pretty quiet, even with the levels way up.  Also when I change the volume I get a popping noise.

---

### Post by tommcd on 2010-02-04
> **Frozen001 said:**
> OK I have it sort of working, but it is pretty quiet, even with the levels way up.  Also when I change the volume I get a popping noise.
Media players have their own volume levels that can act independently of alsamixer. Turn the volume levels up on the media application you are using.
Go to: system preferences > sound, and see what you can find by using the options there. I can't check that for myself, since I have removed pulse audio, so the sound applet under preferences no longer works for me.
Also check the volume levels of your speakers if you have external powered speakers. 
I don't know why you get a popping sound when changing volume levels.

---

### Post by mhgsys on 2010-02-15
@Frozen001


open a terminal ; type

```
sudo gedit /etc/modprobe.d/alsa-base.conf
```

change the line
```
options snd-hda-intel power_save=10 power_save_controller=N
```

into
```
options snd-hda-intel power_save=0 power_save_controller=N
```




[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/442463)

---

