---
title: "bbc and Mplayer .."
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by emacsuser on 2007-11-07
Have installed Mplayer and the plugins as per the below instructions. I get no video on BBC media. Opening a rtsp URL from mplayer gets the same results. What am I missing?

[http://ubuntuforums.org/showthread.php?t=540412](http://ubuntuforums.org/showthread.php?t=540412)

rtsp://rm-acl.bbc.co.uk/drama/robinhood/bb/ep6preview_16x9_bb.rm?BBC-UID=f4e76341cc2fccb818e3b8c2c19aec7aed9b99c66030e1e623d5

---

### Post by OldGrey on 2007-11-07
Hi

Probably no consolation, but I have the same issue having followed the same instructions. I get the sound but the screen remains blank.

---

### Post by Bablefish on 2007-11-07
I have tried Mplayer when it comes to BBC media and let me set the record straight...IT DOES NOT WORK PERIOD 

What you need is Real Player this does work and as far as I tried the only thing that will actually play all Real Player files. You can get it via this terminal command

sudo apt-get install realplayer

---

### Post by emacsuser on 2007-11-08
> **Bablefish said:**
> I have tried Mplayer when it comes to BBC media and let me set the record straight...IT DOES NOT WORK PERIOD

Following another sugestion, I reinstalled Java, went into preferences and changed Realplayer to Windows media player, it played once, now I get nothing on BBC, not even the 'buffering etc' msg, just blank.

This video works except the sound is out of sync and it totally goes out of sync and the video repeats with distortion and then the sound goes out.
[http://stage6.divx.com/TV-Jungle-Music-Videos/video/1110653/Blondie---Heart-of-Glass-](http://stage6.divx.com/TV-Jungle-Music-Videos/video/1110653/Blondie---Heart-of-Glass-)

> **Bablefish said:**
> What you need is Real Player this does work and as far as I tried the only thing that will actually play all Real Player files. You can get it via this terminal command

sudo apt-get install realplayer

'Package realplayer is not available'

I have all the repositeries in I think ...

---

### Post by OldGrey on 2007-11-09
I have just tried installing the W32 codecs available from Medibuntu and they seem to have done the trick.

---

### Post by emacsuser on 2007-11-10
> **OldGrey said:**
> I have just tried installing the W32 codecs available from Medibuntu and they seem to have done the trick.

I installed the codecs, and set it to Windows media player and it works on viewing news videos, it won't work on viewing TV previews just says 'stopped'.

Is the BBC deliberatly sabataging non-MICROS~1 media players ...

---

### Post by OldGrey on 2007-11-11
I've just tried a couple of previews on the BBC website and they worked as well as the news videos for me.

Sorry I don't have an answer for that one.

---

