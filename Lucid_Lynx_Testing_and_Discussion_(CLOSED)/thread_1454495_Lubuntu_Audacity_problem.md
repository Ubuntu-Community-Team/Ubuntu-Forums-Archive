---
title: "Lubuntu Audacity problem"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by RTrev on 2010-04-14
I have most everything I need working fine under Lubuntu, but 
Audacity is giving me problems.

I'll start recording, and within anywhere from a few seconds to a little over a minute, it will simply stop recording.  I can then hit Stop, Play back the recording, save it, and so on.  But nothing I do can induce it to continue recording past wherever it decided to quit.

I see some other threads from earlier releases where people had similar problems, but haven't yet found an answer except to update Audacity.. and I'm running the latest version (1.3.12 Beta) which is the one in the repository.

I've been using Audacity because it gives me the flexibility to make very specific types of recordings which I need in order to convert them to a format a friend uses.  They're mono, 8000 hz, 16 bit, .wav files.  The equivalent command at the console would be:

```

arecord -f S16_LE filename.wav

```

..and this works just fine.

Audacity works fine under Lucid Gnome, but not Lucid LXDE.

Anyone have any ideas?  Even if it's only a place to start looking?  Or perhaps a different lightweight application which can create the type of files I need?  It doesn't have to be fancy, but the command line (arecord) lack of a "pause" feature makes it pretty un-workable for me.  Audacity is way over-kill for my needs, but it's the only one I've found that can do this.

TIA,
Bob

---

