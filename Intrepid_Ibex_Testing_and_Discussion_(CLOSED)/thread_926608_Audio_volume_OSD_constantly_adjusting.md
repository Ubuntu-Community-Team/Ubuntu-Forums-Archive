---
title: "Audio volume OSD constantly adjusting"
date: 2008-09-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by rekado on 2008-09-22
Yesterday (September 21, 2008) I installed the current 8.10 alpha release via "upgrade -d" on my notebook with an Intel HDA sound chip.

Some things are fixed now (such as the broken CPU frequency scaling that I was facing before and some minor issues when booting and shutting down), and I'm happy to say that Ibex has improvements which are subtle but noticable and very useful.

One thing is bothering me, though. When trying to adjust the audio volume via Fn keys the OSD appears and even though I already let go of the key, the volume is still being adjusted gradually till the limit values. Unfortunately upon reaching either maximum or minimum value the OSD does not disappear - it seems as if the key hangs and the command is still submitted. This makes the OSD flicker.
Furthermore I cannot open the main menu anymore from that moment on. Also clicking on the shutdown-applet in the panel does not open the shutdown screen. It all works before adjusting the audio volume via Fn keys, though.

Only killing the X-session with Ctrl+Alt+Backspace resets the OSD and upon logging in another time it all is as it was before.

This bug is reproducable whenever I touch any of the volume adjustment hotkeys (also hotkeys for mute!).

I already filed a bug at launchpad.
Did anyone else face this issue before?
Do you happen to know how to configure the OSD for audio volume?

---

### Post by rekado on 2008-09-25
Still remains even after installing all recent updates.

---

### Post by Sophont on 2008-09-25
Are you sure it's not just your key that's faulty?

You could burn a Hardy live iso and boot that. If the problem is still there it's likely your key that's broken, otherwise it's a bug.

---

### Post by rekado on 2008-09-25
I've been using Ubuntu since a long time. Right after I upgraded to Intrepid the keys showed this behavior. I don't have an empty CD here at the moment but I sure will try.

---

### Post by rekado on 2008-09-25
So, there is more to it:

I ran xev in the terminal to check if the command is sent repeatedly. It is not. When running xev and performing either shortcut the OSD appears increments or decrements one step and disappears again. However, the panel still becomes unusable. Also typing in the address bar of firefox won't work anymore, Alt+Tab doesn't switch windows anymore (I do not use Compiz) etc.

Another thing is that without running xev the constant change of the OSD can be interrupted by pressing Esc. Still I would lose interaction with the system as described above.

So it's definitely not the keys.

---

### Post by rekado on 2008-09-26
I filed a bug:
[https://bugs.launchpad.net/ubuntu/+bug/273009](https://bugs.launchpad.net/ubuntu/+bug/273009)

---

### Post by rekado on 2008-10-06
Even after a complete reinstall with the current Intrepid Ibex Beta ISO the problem remains.

---

### Post by djcslip on 2008-10-15
Exactly the same here - any ideas?

---

### Post by rekado on 2008-10-15
You could subscribe to the bug in launchpad and comment there to confirm the bug and draw the developers' attention to it.

---

### Post by noOneSpecial on 2008-10-15
Sounds like this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706)

---

### Post by rekado on 2008-10-16
> **noOneSpecial said:**
> Sounds like this bug
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706)

Seems that you are right. The bug description sounds very similar. I marked my bug as a duplicate. Comments on the other bug report suggest that this is caused by the new driver evdev.

---

### Post by noOneSpecial on 2008-10-16
Yeah looks that way. My volume keys are doing the same thing. Ubuntu was the only distro I'd tried where they worked, oh well.. no big deal to change the key combos for now. :)

---

