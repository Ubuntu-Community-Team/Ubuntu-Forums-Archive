---
title: "No sound Intel NUC"
date: 2016-09-25
forum: Installation &amp; Upgrades
---

### Post by zkab on 2016-09-25
I have Xubuntu 16.04.1 LTS (4.4.0-38-generic) running on a Intel NUC (DC53427HYE) that is hooked to my Samsung TV.
It has been working OK for a long time but suddenly there was no sound (HDMI).
I replaced the no-sound-NUC with another NUC and the sound was there - so apparently the TV setup was OK.
Then I upgraded the no-sound-NUC firmware the the latest (RK0043.bio) but still no sound.
So I began to suspect a hardware problem - but I gave it a last try.
I booted with a live USB Ubuntu 16.04 and ... bingo ... the sound was there ... apparently no hardware issue.
Some software is creating the problem with the sound.
I am totally lost and really need support to fix this issue - don't know where to start to eliminate the problem step by step.
All help is very much appreciated.

---

### Post by sudodus on 2016-09-25
Start the control panel for audio, pavucontrol, "Volymkontroll". Run an audio file or video file, and while it is running, tweak the various settings in different tabs, and listen - I think that after a while, you will find a setting that makes it play sound again. It is worth trying for a long time - remember to keep the computer playing [audio], otherwise there is no feedback and you will not notice that you have found the correct setting.

Exactly what it looks like and how it works depends on the hardware in your particular computer, so it is hard to give detailed step by step tips. Maybe you can compare with the settings in the live session, where it works, and try to get those settings also in the installed system.

-o-

If you have bad luck, a kernel upgrade might have brought a bad audio driver, a driver that does not work with your hardware. In that case you can hope that the next upgrade will make it work again, or if you have the time, ***report a bug*** about it at Launchpad. If nobody reports a bug, the developers will never know that there is a bug.

---

### Post by zkab on 2016-09-26
I followed your recommendation and discovered that somehow in the tab 'Output Devices' the sound was muted ... don't ask me why this was set to mute ... I have not done it.
Maybe it was set by some software by mistake ... anyhow now I am airborne again.
Thanks for you help.

---

