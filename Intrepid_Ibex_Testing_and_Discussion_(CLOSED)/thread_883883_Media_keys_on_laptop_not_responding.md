---
title: "Media keys on laptop not responding"
date: 2008-08-08
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by phenest on 2008-08-08
I can set all my media keys (volume up/down, next, previous, play/pause, etc) to actions in keyboard shortcuts, but none of them respond. I can set them directly into Exaile, but again, they do not respond.

Volume up/down are the only ones that work.

Anyone else?

My laptop is the one in my signature.

---

### Post by raul_ on 2008-08-08
Check if they produce anything in xev.

First you need to install xev.

then, in a console, type 'xev', press your media keys, and check if they produce a keycode.

---

### Post by hvac3901 on 2008-08-08
> **raul_ said:**
> Check if they produce anything in xev.

First you need to install xev.

then, in a console, type 'xev', press your media keys, and check if they produce a keycode.

That is cool!

---

### Post by phenest on 2008-08-08
> **raul_ said:**
> Check if they produce anything in xev.

I already did that, and they all work correctly with the correct keycodes.

---

### Post by raul_ on 2008-08-08
Well, maybe you could try and set them up with xbindkeys.

I'm not sure why they don't work with the global shortcuts though

---

### Post by Benjamin_Lebsanft on 2008-08-08
open keyboard properties under System -> Preferences, reset to default values (maybe reboot) and set the hotkeys via System -> Preferences -> Shortcuts. Worked for me.

---

### Post by phenest on 2008-08-08
Already done that too.

---

### Post by Nullack on 2008-08-09
So whos bugged it and what is the number? :)

---

### Post by caryb on 2008-08-09
It's funny but my T61 extra keys started working today:)



Cary

---

### Post by kiisu on 2008-08-11
What's weird is that this issue was one of the few that stumped me when I was starting out w/ Ubuntu earlier this year.

Just had some time to kill and took another look at it .... after following some of the leads here in this thread and adjusting shortcuts both within my system and in Amarok, suddenly my play/pause button works, as well as my connect-to-the-net button (sorry for the non-technical terms haha).

 But following the same directions did nothing for the stop, and skip forwards & backwards buttons....

Guess I'll keep poking around and report back if I hit a breakthru

---

### Post by phenest on 2008-09-13
Launchpad bug: [267495]("https://bugs.launchpad.net/ubuntu/+source/xkeyboard-config/+bug/267495")

---

### Post by beercz on 2008-10-14
I don't know if it is related, but I have also discovered that my mute button doesn't work, but my volume up and volume down buttons work fine.

Anyone else found this?

---

### Post by phenest on 2008-10-15
Must be the same bug, 'cos I have that problem too.

---

### Post by PsychedelicReaction on 2008-10-20
It looks like i have the same problem. Volume up and down + mute are working correctly system wide. Prev/next track, stop, play/pause work only with totem. My laptop is a Dell XPS1330m.

---

