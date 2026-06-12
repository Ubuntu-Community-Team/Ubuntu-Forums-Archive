---
title: "Amarok not working: no sound, no ipod ?"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TimT on 2009-10-24
Hi,

 For some reason Amarok is not working on my current install:

1. when I click a song, nothing happens. It just loads some band/song related info from the internet, but no sound comes out. (play button changes from play to pause and back almost instantly). Checking playback set up, everything seems OK, and the test button works fine on all outputs. (Though I can't select the gstreamer output.)

 Banshee plays just fine (just noticed that audacious2 crashes on start up.. Hmm) Exaile is OK too. 

2. Neither banshee or Amarok seem to see my ipod classic at present. gtkpod can open it, and everything seems OK (Except it wants to play the music using audacious, which crashes.. hmmm. How do I change that ?)

Suggestions are welcome..

---

### Post by seeker5528 on 2009-10-24
> **TimT said:**
> Hi,

 For some reason Amarok is not working on my current install:

1. when I click a song, nothing happens. It just loads some band/song related info from the internet, but no sound comes out. (play button changes from play to pause and back almost instantly). Checking playback set up, everything seems OK, and the test button works fine on all outputs. (Though I can't select the gstreamer output.)

Sounds a lot like there is missing codec support.

For Amarok you should have phonon-backend-xine installed, which I'm guessing you already have, along with libxine1-plugins. Should also have libfaad0 and libfaac0 if you need m4a support.

If you are using the Xine backend, you might try installing the phonon-backend-gstreamer and switching to it. Typically it seems to be a little more quirky than the xine backend, but YMMV.

Later, Seeker

---

