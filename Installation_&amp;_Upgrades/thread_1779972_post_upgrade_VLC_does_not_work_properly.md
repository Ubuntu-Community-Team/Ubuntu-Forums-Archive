---
title: "post upgrade VLC does not work properly"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by avidesh on 2011-06-11
Post upgrade to 11.04 I can not view video in VLC. I get the audio but not video when I try to run the command
```
dvgrab - | vlc - --no-sub-autodetect-file
```.

I get following error

No suitable decoder module:
VLC does not support the audio or video format "dv  ". Unfortunately there is no way for you to fix this.

Please suggest what I need to do.

---

### Post by Herman on 2011-06-11
I just upgraded too and haven't tried my vlc media player yet. 
Maybe try uninstalling your vlc media player and re-installing it again, it could be that might fix some broken dependency problem with a little luck. 
I would use synaptic package manager to do that, open synaptic package manager and search for vlc, it should be an easy job from there.

---

### Post by avidesh on 2011-06-12
that did not work. I get the same error message.

---

### Post by Herman on 2011-06-12
[URL="http://linux.die.net/man/1/dvgrab"]
[/URL]

---

