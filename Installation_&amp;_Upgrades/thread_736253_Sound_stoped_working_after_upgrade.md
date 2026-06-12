---
title: "Sound stoped working after upgrade"
date: 2008-03-26
forum: Installation &amp; Upgrades
---

### Post by Paracelsus on 2008-03-26
I just upgraded from Ubuntu 7.4 to 7.10 and my sound stopped working. I get this error when I try to use a sound.

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open resource for writing.

and also this error

No volume control GStreamer plugins and/or devices found

any ideas?

---

### Post by Metaljaz on 2008-03-26
Read here:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

Post the output of this command:

sudo lshw -C sound

---

