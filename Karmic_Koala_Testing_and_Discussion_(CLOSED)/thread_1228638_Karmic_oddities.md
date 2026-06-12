---
title: "Karmic oddities"
date: 2009-08-01
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ELDal on 2009-08-01
So far 9.10 has been great no major breakage here (yet). Still I've noticed a few things in karmic that's behaving strangely.

Pulse-audio: Every time a new sound source is added all other ALSA plug-ins have their output turned all the way down.

Windows shares: can't seem to be able to copy any files from a windows box anymore, copies the file then gives a "invalid argument" right before it finishes and the file turns up corrupted.

desktop icons: they are huge, really huge. By pressing restore icon's original size it becomes normal.

Could someone see if they can replicate these oddities? :)

---

### Post by Hairy_Palms on 2009-08-01
+1 for the pulseaudio, pulseaudio is a trainwreck.

---

### Post by buzzmandt on 2009-08-01
funny thing is I'm using pulseaudio in kubuntu karmic and except for a little bit of skipping at times it works flawless.

---

### Post by tekstr1der on 2009-08-01
> **ELDal said:**
> 
Windows shares: can't seem to be able to copy any files from a windows box anymore, copies the file then gives a "invalid argument" right before it finishes and the file turns up corrupted.


Yeah, this one hurts. I am unable to downgrade libsmbclient, so I hope this fix comes soon.

[https://bugs.launchpad.net/gvfs/+bug/393012](https://bugs.launchpad.net/gvfs/+bug/393012)

and upstream: [http://bugzilla.gnome.org/show_bug.cgi?id=588391](http://bugzilla.gnome.org/show_bug.cgi?id=588391)

---

