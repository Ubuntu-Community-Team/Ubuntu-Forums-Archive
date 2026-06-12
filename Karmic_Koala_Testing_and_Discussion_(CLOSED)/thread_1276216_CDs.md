---
title: "CDs?"
date: 2009-09-26
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by oboedad55 on 2009-09-26
I'm having a problem with CDs. I can insert one okay but after I eject it the tray won't physically close. Also having a problem playing CDs with Rhythmbox anyway. I haven't tried them with another player. They won't play, as if they're not recognized.

---

### Post by grumpymole on 2009-09-26
Same here.  Rhythmbox won't play CDs.  It recognises them and must be able to read something to download the track data, but can't play.

Could be [this bug]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/431027") or [this one]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035").

Cheers

---

### Post by oboedad55 on 2009-09-26
> **grumpymole said:**
> Same here.  Rhythmbox won't play CDs.  It recognises them and must be able to read something to download the track data, but can't play.

Could be [this bug]("https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/431027") or [this one]("https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/435035").

Cheers

It could be the second one. I'm having the problem regardless of player. I tried Banshee with the same effect.

---

### Post by ranch hand on 2009-09-27
You know, I have been guilty of not testing everything that I normally use.

When I set up any new OS I copy my music library over to it from my main.  I have never, until I saw this thread, tried to play a cd on 9.10.

Sure enough, it doesn't work.

I get to errors, one about "cdda" and the other about the "pipeline".  Niether of which make any sense to me.  I will study on this in the morning.  I have a search engine.

Apport  is not picking this up automatically.

---

### Post by oboedad55 on 2009-09-27
> **ranch hand said:**
> You know, I have been guilty of not testing everything that I normally use.

When I set up any new OS I copy my music library over to it from my main.  I have never, until I saw this thread, tried to play a cd on 9.10.

Sure enough, it doesn't work.

I get to errors, one about "cdda" and the other about the "pipeline".  Niether of which make any sense to me.  I will study on this in the morning.  I have a search engine.

Apport  is not picking this up automatically.

Okay, that sounds like the errors I'm getting as well.

---

### Post by ranch hand on 2009-09-28
I ran a search for cdda in karmic and came up with this;

[http://packages.ubuntu.com/karmic/libcdio-cdda-dev](http://packages.ubuntu.com/karmic/libcdio-cdda-dev)

Checked in synaptic and it was there.  Did an apt-get install to make sure to get any other packages I may need.

Still doesn't work.  I am going to reboot and see if that helps.

edit

Nope.

Apport finally noticed the problem but could not report it and quit.

---

