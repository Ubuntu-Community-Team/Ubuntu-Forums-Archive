---
title: "PulseAudio does not display hardware sink"
date: 2009-09-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hexsel on 2009-09-08
I just updated about a week's worth of updates, and I find that pulse does not list any sinks except for auto_null.  I tried padevchooser, but the same problem occurred.  Pulse does seem to display the sound as playing though.  Anyone had this problem?

---

### Post by fab.head on 2009-09-12
Hi hexsel

Please see whether your issue is similar to the one which I described here:
[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500")

If so, you could subscribe to this bug as well.

---

### Post by fab.head on 2009-09-13
It seems that the issue could be caused by the softmodem driver.
If you have activated it in System > Administration > Hardware Drivers , try to deactivate (Remove) it.

More info at [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/394500")

I know it's just a workaroud and not a real solution, but at least it works for me for the time being.

---

