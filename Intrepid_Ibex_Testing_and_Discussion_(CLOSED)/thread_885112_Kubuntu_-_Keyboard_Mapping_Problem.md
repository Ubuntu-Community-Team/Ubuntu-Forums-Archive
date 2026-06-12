---
title: "Kubuntu - Keyboard Mapping Problem"
date: 2008-08-09
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by tripinva on 2008-08-09
I had a series of problems which are now mostly fixed, except for this latest one.

Permissions on / got changed so I couldn't use sudo, in order to fix this I had to reboot into recovery and do a chmod, then X would start and the keyboard wouldn't work at all.  Finally it started working by itself, nothing I did fixed it, but the keyboard layout's screwed up.  At kdm, it's correct, but once I log it, it's very wrong.

Examples:

Right Alt = Enter (should be Compose key--it even says so in System Settings)
Home = / (or ' if shift is held)
PgUp = Left Windows Key

Also not working:  Arrow keys, End, PgDn, Delete...

So I don't know quite what to do with it.  Everywhere I look it's set to be "US" but it's acting like it's not.

- Trip

---

### Post by ubulette on 2008-08-10
Map your keyboard to 'evdev'.

Under Gnome, System/Preferences/Keyboard, then Layouts, Keyboard model, select "Evdev-managed keyboard". Close and you're done.
No idea under KDE.

You can also achieve this using "setxkbmap -model evdev ...."
and your layout, variant, etc.

See [https://launchpad.net/bugs/255008](https://launchpad.net/bugs/255008)

---

### Post by LN2 on 2008-08-10
In KDE it is System Settings -> Regional & Language-> Keyboard Layout -> then select under "Keyboard Model" Evdev-managed keyboard.

---

### Post by caryb on 2008-08-11
I tried LN2's advice & changed my keyboard to IBM T61 now I don't have any arrow keys & volume keys are stuffed again, I reverted back to generic 104 keys & same problem. I even tried the reset function but no joy! I was going to file a bug report but what in the heck do I file it against:confused:


Cary

---

### Post by tripinva on 2008-08-11
Thanks!

This fixed almost every problem I was having--even my media keys are working properly once more.  I had been using XModMap to map my keys, but this is much better. =)

The only remaining issue is that the global shortcuts to adjust volume in KMix seem to have stopped working.  Other than my volume controller on my machine, I'd also mapped Ctrl+Alt+PgUp/PgDn to volume.  Neither control works...

- Trip

---

### Post by fenrisswolf on 2008-08-30
Nice fix!  

I kept having this problem intermittently, (whenever I reloaded the Xserver, mainly,) and knew it had to be a key mapping issue, since the qwerty keys worked properly, but I had no clue how to fix it.

---

