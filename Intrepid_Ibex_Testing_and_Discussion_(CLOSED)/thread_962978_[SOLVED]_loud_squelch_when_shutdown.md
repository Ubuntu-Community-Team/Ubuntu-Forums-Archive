---
title: "[SOLVED] loud squelch when shutdown"
date: 2008-10-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by stormtrooprdave on 2008-10-29
When i select shutdown from the panel and confirm it I get a loud squelch from the internal speaker.  Does this happen to other people too and how can I disable it?

---

### Post by inportb on 2008-10-29
Does this happen if you disable the internal speaker?

---

### Post by stormtrooprdave on 2008-10-30
Turned off the internal speaker using advice from [this thread]("http://ubuntuforums.org/showthread.php?t=948892&highlight=beep+blacklist") and it no longer beeps

> **carney1979 said:**
> Try this:

From a Gnome-Terminal:

```
sudo gedit /etc/modprobe.d/blacklist
```Scroll to the end of the file and enter:

```
blacklist pcspkr
```Save the file, exit gedit.

then in the terminal type:

```
sudo rmmod pcspkr
```You should never hear that system beep again when you shut down. 

Upon any further system startups the line you added in the blacklist file will keep the pc speaker's module from being loaded.

Worked for me.

David

---

### Post by ercdvs on 2008-10-30
what is the actual cause of this, rather then just resorting to turning off the system speaker ?

---

### Post by inportb on 2008-10-30
I am not sure. But I blacklist that module anyway as I find the system beep annoying in other situations as well.

---

### Post by shane19174 on 2008-10-30
Following a lead from another thread, I tried using the new "fast user switcher" thingy instead of the old shutdown button (which I had been using) and found that the beep disappeared. Again, the normal shutdown button that I either retained on my system when upgrading from Hardy or which I added later (I can't recall) seems to be the culprit. Using the now-standard user switcher, there is no beep.

---

### Post by PinkFloyd102489 on 2008-10-30
Even when I disabled the pcspkr module, mine still beeped. It hasnt done so in about a week now, but Im waiting for it to go ballstic during class again.

---

