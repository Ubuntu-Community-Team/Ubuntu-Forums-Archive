---
title: "Upgrade to 10.10 broke my surround sound, no 5.1, only stero."
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by callecx on 2010-11-07
Hi,


 I upgraded my ubuntu installation from 10.04 to 10.10, now surround sound (5.1) does not work in xbmc, or in another player such as vlc. Only the front two speakers work.

 I noticed pulseaudio and alsa are installed. I thought i removed pulseaudio once before but cant really remember.
 In the sound configuration preferences thing (prefs >> sound), i  have hdmi output selected (hdmi goes from the HTPC to the amplifier).  It only plays audio in 2.0 instead of 5.1. I tried selecting the analog 5.1 sound option, but none of the test sounds work. However i noticed vlc still played movies with audio, but only stero no 5.1. 

 Previous to the upgrade, i had 5.1 working fine in xbmc, never bothered to check vlc since it was all good.
 Also, when i go into alsamixer, it does not show any rear speakers,  it just shows a front speaker and a bunch of other stuff, like  headphones.
 Any ideas? I'm not sure what other output you guys need, but let me know and i'll get it.
 Here is the alsa-info.sh output for my HTPC:
[http://www.alsa-project.org/db/?f=2393aae09221a123b72c5f7d48a078341f204b22](http://www.alsa-project.org/db/?f=2393aae09221a123b72c5f7d48a078341f204b22)


[URL="http://www.alsa-project.org/db/?f=2393aae09221a123b72c5f7d48a078341f204b22"]Another note, after i reinstalled pulseaudio the first time, vlc fails to display a 5.1 movie and still plays tero output. 
[/URL]


[URL="http://www.alsa-project.org/db/?f=2393aae09221a123b72c5f7d48a078341f204b22"]any ideas? 
[/URL]

---

### Post by callecx on 2010-11-07
Also, when i run alsa speaker-test -c 6, the left and right speakers play their sounds as they are supposed to. Although when it comes to the centre and rear speakers, it simply plays the tone out of both and front two.

---

### Post by mack1986 on 2010-11-17
Solved the problem with Realtek ALC1200 in ubuntu 10.10 64bit with 5.1 sound
Just typed alsamixer in terminal and ajusted the volume.

---

