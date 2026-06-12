---
title: "Can't get MIDI working"
date: 2006-09-05
forum: Installation &amp; Upgrades
---

### Post by theosib on 2006-09-05
I seem to be completely unable to get MIDI working.  I've done some googling around, but I haven't gotten much help.  I do know that my hardware doesn't support it directly, so I found heard about something called "Timidity", which I installed using Adept.  Installing Timidity didn't seem to do anything at all.  There's no new menu entry, and KDE's "Test MIDI" still doesn't do anything.

Help?

---

### Post by tatimmer on 2006-09-05
"tomstimiditytips" may help.

 I use the command line version of timidity so there is no gui menu entry.  If you just type the word "timidity" into a gnome-terminal what happens ?  Have you installed a set of sound patches ?  Timidity converts your midi file to a wave file "on the fly" using sound patches which are available from [http://freepats.opensrc.org/freepats-20040611/](http://freepats.opensrc.org/freepats-20040611/)

---

### Post by Nonno Bassotto on 2006-09-05
[This link]("https://help.ubuntu.com/community/MidiSoftwareSynthesisHowTo") describes in detail the (few) steps you need to follow after having installed timidity. (I think you don't have to worry to install a soundfont, since now timidity is installed with freepats (a free soundfont) by default.

Probably you just need the last step, that is, to uncomment the line
```

TIM_ALSASEQ=true

```
in the file /etc/default/timidity.

---

### Post by theosib on 2006-09-05
Thank you for that help.  It seems that I have it mostly working, because I can play midi via kmid.  However, the KDE Sound & Multimedia "Test MIDI" button still does nothing.  It would seem that KDE still isn't configured right.  I do have "TiMidity port 0 - ALSA device" configured as the hardware, however.

---

