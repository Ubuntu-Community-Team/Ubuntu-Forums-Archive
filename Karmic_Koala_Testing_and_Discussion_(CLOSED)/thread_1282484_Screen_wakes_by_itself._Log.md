---
title: "Screen wakes by itself. Log?"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Zorael on 2009-10-04
I can't keep my monitor on standby/suspended/powered off.

If I tell KDE to automatically suspend it after n minutes, then it does suspend properly. But after another couple of minutes, it wakes and resets the suspend timer.

If I use xset to force the screen to suspend or shut down, it wakes immediately. To rule out the keyboard input event of hitting enter (to run the command) cancelling it out, I delayed it with sleep, but it still wakes after less than a second.
```
$ sleep 5; xset dpms force off
```

On #ubuntu+1, I was told by yofel who was running the same KDE environment on the same hardware (Intel 945GME) that he could force it off properly. I'm not really running any app that could be waking it up, either.


Is there a way to make X log when and why it sends the monitor to sleep, and when and why it wakes it up? Xorg.0.log didn't say anything of interest, at least not on the default log verbosity level.

---

