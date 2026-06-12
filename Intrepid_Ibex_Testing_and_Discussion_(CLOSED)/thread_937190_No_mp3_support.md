---
title: "No mp3 support"
date: 2008-10-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Ewingo401 on 2008-10-03
Hey guys.  For some reason I can't get 8.10 to play mp3 files even with the restricted extras installed.  I even tried reinstalling them from synaptic with no luck...any ideas?

---

### Post by durand on 2008-10-03
Try using a different media player.
```
sudo aptitude install mplayer
```
then right click on a file and run with Mplayer.

Just to see if it works or not.

---

### Post by forger on 2008-10-03
what does it say in the terminal when you play a file:
```
totem /path/to/your/file.mp3
```

---

### Post by Ewingo401 on 2008-10-03
> **durand said:**
> Try using a different media player.
```
sudo aptitude install mplayer
```
then right click on a file and run with Mplayer.

Just to see if it works or not.


Interesting...it works on mplayer.  It also unsurprisingly works with vlc.  However it won't play from totem, straight from nautilus, and most importantly it won't play from rhythmbox my music player of choice.  Any other ideas?

---

### Post by durand on 2008-10-03
Try what forger said...(replace totem with rhythmbox) Hopefully, it gives errors.

---

### Post by SuperSonic4 on 2008-10-03
Try changing RB's sound output to something else?

I've no idea how to do it though, I never used rhythmbox always amarok here

---

### Post by Ewingo401 on 2008-10-03
> **forger said:**
> what does it say in the terminal when you play a file:
```
totem /path/to/your/file.mp3
```


It says "An error occured.  Failed to connect stream:  Invalid argument."

---

### Post by howefield on 2008-10-03
are the mp3 files being accessed through a samba share ?

---

### Post by durand on 2008-10-03
> **Ewingo401 said:**
> It says "An error occured.  Failed to connect stream:  Invalid argument."

Seems like that error isn't related to MP3s...Try it with a different music file in the same place.

---

### Post by Ewingo401 on 2008-10-03
No samba share.  And also I just found something interesting.  I also can not play .ogg files in totem or rhythmbox.  So it doesn't appear to be a codec issue.  Anybody got any other ideas with this new info?

---

### Post by taavikko on 2008-10-03
> **SuperSonic4 said:**
> Try changing RB's sound output to something else?

I've no idea how to do it though, I never used rhythmbox always amarok here

when using gstreamer- backend you caan change the settings via
```
gstreamer-properties
```

---

### Post by andrewabc on 2008-10-03
Maybe it is a problem with the default audio setting in the program such as using ALSA or pulseaudio? conflicting with your soundcard setting in sound options?

---

### Post by Ewingo401 on 2008-10-03
> **andrewabc said:**
> Maybe it is a problem with the default audio setting in the program such as using ALSA or pulseaudio? conflicting with your soundcard setting in sound options?

I thought about that and went in and manually set everything to pulse audio where it wasn't already set and had the same issue.  I then tried to set everything to alsa and still was left with no playback.  I'm not sure whats going on with this one.  I'm back on 8.04 for the time being.  I'll give 8.10 another try when the official release hits.

---

### Post by DougieFresh4U on 2008-10-03
> **Ewingo401 said:**
> No samba share.  And also I just found something interesting.  I also can not play .ogg files in totem or rhythmbox.  So it doesn't appear to be a codec issue.  Anybody got any other ideas with this new info?

Just a thought, I had problem with amarok saying couldn't play mp3 and I had 'Ubuntu extras' installed. So I went into Add/Remove and searched and found something related to different music files and i checked the box and applied it and mp3's played. not sue what one it was, or if it will help you but a thought any ways.

---

### Post by forger on 2008-10-04
> **Ewingo401 said:**
> I thought about that and went in and manually set everything to pulse audio where it wasn't already set and had the same issue.  I then tried to set everything to alsa and still was left with no playback.  I'm not sure whats going on with this one.  I'm back on 8.04 for the time being.  I'll give 8.10 another try when the official release hits.

Go to system > preferences > sound again, set *everything* to pulseaudio, then press close and reboot the computer, you'll get better results when gnome is restarted (if you want the geek way, log out, press ctrl-alt-F1, login in console, and use: sudo /etc/init.d/gdm restart )

Then log back in and check if the sound works, if it doesn't work, set *everything* to alsa, and repeat for all of them until you find one that works :)

---

### Post by Wubuntish on 2008-10-04
My guess is that it is a Gstreamer issue in connecting to PulseAudio. 1st post of the following thread fixed the issue for me:

[HOWTO: PulseAudio Fixes (distilled) - *Updated, Call For Testing!*]("http://ubuntuforums.org/showthread.php?t=866965")

---

### Post by MALEADt on 2008-10-04
I got this error too after updating to intrepid's beta. Latest updates however seemed to fix this problem.

---

