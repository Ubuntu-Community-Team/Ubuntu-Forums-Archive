---
title: "Can't play OGG vorbis"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by readams on 2009-03-25
I can't play any OGG music through anything using gstreamer.  MP3s play OK.  Playing through mplayer also works fine. 

In Totem, attempting to play OGG pops up a message "pa_stream_proplist_update() failed: Not supported"

This is on a system recently upgraded from intrepid.  Has anyone seen this before?  I couldn't find anything in a Google or forum search.

---

### Post by taavikko on 2009-03-25
Could you host a sample for us wierdo's to have a look :)

---

### Post by KCG102282 on 2009-03-25
File a [bug report]("http://launchpad.net/ubuntu")

---

### Post by taavikko on 2009-03-25
> **KCG102282 said:**
> File a [bug report]("http://launchpad.net/ubuntu")

Issue just might be cruft settings after the release-upgrade

Like ~/.asoundrc ~/.pulse/ which I would recommend removing and then testing again. (rm before logging in )

---

### Post by readams on 2009-03-25
Apparently it's only when you're using a remote pulse server also.  So only when using remote server and playing OGG vorbis streams.

---

### Post by readams on 2009-03-25
Here's a screenshot.

Deleting .pulse* from console and logging in didn't fix the problem

---

### Post by readams on 2009-03-25
Bug report
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348540](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/348540)

This might be gstreamer and not pulse, but I filed against pulse.

---

### Post by readams on 2009-03-25
I was able to resolve this problem by upgrading also the system that was receiving the sound.

---

