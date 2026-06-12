---
title: "ICH8 audio - hiss; also channels linked to each other"
date: 2010-04-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jrial on 2010-04-07
Since upgrading to Lucid, I'm experiencing problems with the ICH8 audio which worked perfectly under Jaunty and Karmic. The problem is twofold:

First of all, when I use the gnome volume settings to change the master volume (doesn't offer me a lot of choices: master, balance, fade and subwoofer), the subwoofer slider moves along.

And the second problem is that when the master/subwoofer levels are not at 100%, I get noticeable hiss in flash audio. The hiss disappears when I slide the levels to 100% and set the "ALSA plug-in [firefox-bin]" setting in the "Applications" tab to a really low value to avoid oversampling.

My soundcard is detected as follows:
```
Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
```

Sometimes I can also get the hiss to disappear when I use alsamixer to set the levels, although alsamixer gives me a completely different set of controls. But in alsamixer too, levels are inexplicably linked together. For example: I can not get PCM below 98%; Front, Surround, Center, LFE and Side go down to 94% before resetting to 100%, at which point Master goes down a notch and this cycle repeats until Master is at 0%, at which time I can control the individual channels again. However, turning them all up does not produce sound, only messing in the gnome audio controls gets me my sound (including hiss) back.

Definitely something going on that messes with Alsa. If anyone has any pointers, feel free to share. :)

---

