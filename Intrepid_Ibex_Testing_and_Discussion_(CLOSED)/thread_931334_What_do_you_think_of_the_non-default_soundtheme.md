---
title: "What do you think of the non-default soundtheme?"
date: 2008-09-27
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olskar on 2008-09-27
Hi,
I noticed that the soundpreferences has been improved and now supports soundthemes :) I also noticed that you can use another soundtheme then Ubuntu. I actually like it better then those jungle drum... what do you think?

---

### Post by phenest on 2008-09-27
They've only changed 2 sounds: login and logout

But there are still login sounds that can be set in System>Administration>Login Window - Accessibility tab

Also, if you change one sound to Disabled, the rest stop working.

---

### Post by ripps818 on 2008-09-27
It seems sound effects aren't working for me. Pusleaudio is working though, I'm still able to listen to music through mpd.

---

### Post by psyke83 on 2008-09-27
> **ripps818 said:**
> It seems sound effects aren't working for me. Pusleaudio is working though, I'm still able to listen to music through mpd.

Are you sure that PulseAudio works properly? If MPD is run system-wide, it will fallback to ALSA. If that happens, PulseAudio will fail to grab the audio hardware, because PulseAudio is configured to run on a per-user basis upon login.

---

