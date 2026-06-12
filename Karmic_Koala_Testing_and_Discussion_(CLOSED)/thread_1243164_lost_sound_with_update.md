---
title: "lost sound with update"
date: 2009-08-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kaitwospirit on 2009-08-18
An update that happened in the past 24 hours took out my sound. I didn't even register an update to anything sound-related, but maybe I missed it. Does anyone else have this problem, or a suggestion of what package could be causing these issues?

---

### Post by psyke83 on 2009-08-18
Your sound may be fine, but a mixer (or application mixer) is muted.

See the Volume Control properties for the Output Devices and Applications, and:

```
$ alsamixer -Dhw
```

P.S. Kernel updates are also related to sound, don't forget.

---

### Post by kaitwospirit on 2009-08-18
Thanks, but playing with the sound preferences didn't work. I did manage to get sound going again by restarting pulseaudio, however (pkill pulseaudio followed by pulseaudio -vv).

So... it's a pulseaudio issue.

---

### Post by wfp on 2009-08-18
Thanks Psyke83 I wanted to give the alpha another spin. I installed gnome alsa-mixer and noticed front was muted. Also checked headphone-rebooted, and now have sound. When I take a new car for a spin I like to have my stereo on. Thanks  Update so I find on reboot, or logging off my headphones need to be re-ticked in alsa. easy fix.

---

