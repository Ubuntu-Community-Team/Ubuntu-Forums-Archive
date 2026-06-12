---
title: "Digital sound out not working without begin able to restart Alsa"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aVirulence on 2010-03-13
So if I understand it correctly, PulseAudio is no longer using Alsa. Well, my problem is the following. For a while now (I'd say since the release of Ubuntu 9.10) I had to jump through hoops to get digital audio working. This was my normal 'game-plan':

[LIST=1]
[*]Turn audio set off
[*]Turn audio set on
[*]Restart /etc/init.d/alsa-utils (or something similar)
[*]Kill pulseaudio (which would automatically restart)
[/LIST]

At that time, I would hear a 'pop' from my speaker, meaning for me that sound would work as of this moment. However, since 10.04 doesn't allow me to restart Alsa, my sound doesn't work at all. 

I'm not sure what was wrong in the first place, but I was willing to follow the steps I described above to get sound working... Any suggestions as to how I can get my sound working again? 

By the way: if I choose the analog audio profile from the sound preferences dialog, I get audio over my headset. When set to digital audio, I hear nothing from my audio set. Alsamixer shows that the digital audio channel is not muted.

---

