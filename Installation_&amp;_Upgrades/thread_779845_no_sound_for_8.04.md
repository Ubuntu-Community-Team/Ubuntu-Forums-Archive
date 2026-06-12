---
title: "no sound for 8.04"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by magicsmoke on 2008-05-03
Installed 8.04 from CD but I get no sound at all, not even the login screen or desktop loading music.  My volume control is automatically muted from startup and when I open volume control, it only shows 1 volume bar for Recording/Microphone.

BIOS shows onboard sound is enabled.

Running the sound tests in System->Preferences->Sound all give an error such as:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Failed to connect stream: Invalid argument
```


Sound worked fine for me for all previous Ubuntu releases.  Any help or suggestions would be much appreciated.  Thanks.

---

