---
title: "Onboard Beep"
date: 2005-07-21
forum: Installation &amp; Upgrades
---

### Post by eelozano on 2005-07-21
How can I disable this.

I get an onboard audio beep every time I backspace too much on a Terminal.

Since I use the terminal a lot and I have a bad habit of hitting backspace too many times I am getting this beep in the middle of class and its just a bit irritating.

Any help is appreciated.

---

### Post by javiadip on 2005-07-21
[QUOTE=eelozano]How can I disable this.

I get an onboard audio beep every time I backspace too much on a Terminal.

Since I use the terminal a lot and I have a bad habit of hitting backspace too many times I am getting this beep in the middle of class and its just a bit irritating.

Any help is appreciated.[/QUOTE]

i do that too all the times, i dont think there is any other way then to mute it.

---

### Post by eelozano on 2005-07-21
I guess I'll live with it.  It does have a comedic effect since nobody can really tell where its coming from...so this kid in the front of class keeps looking at the cieling with the most idiotic face I have ever seen.

Makes it worth it :)

---

### Post by mctavish on 2005-07-21
There should be lots of info on this in the forums.

One way to do it is to put this command:

```
xset -b
```

into a file that is read when your system starts up. This will stop all system beeping while using x windows.

I have a non-standard install so I know what works for me:  ~/.xsession but I'm not sure that this file is read when using gdm.

Another approach I've discovered recently is to stop the computer speaker module loading on boot. This means that the computer doesn't beep while shutting down which is very nice for a quiet freak like me.

I put this line:

```
pcspkr
```

into this file: /etc/hotplug/blacklist

Not sure if this module is applicable for all pcs though.

Anyway, enough rambling. Short answer: use the search button.

---

### Post by eelozano on 2005-07-22
Those looking for a solution for the current release (Hedgehog 5.04)


System -> Preferences -> Sound

Just a little different from the last release.

---

### Post by SWAT on 2005-08-08
[QUOTE=eelozano]Those looking for a solution for the current release (Hedgehog 5.04)


System -> Preferences -> Sound

Just a little different from the last release.[/QUOTE]

This isn't meant to flame/troll whatever, but try to remember that Ubuntu has a default installed Gnome. People such as I install something else afterwards (like fluxbox). The "xset -b" worked fine for me :-)

---

### Post by eungkyu on 2005-08-08
[QUOTE=eelozano]Those looking for a solution for the current release (Hedgehog 5.04)


System -> Preferences -> Sound

Just a little different from the last release.[/QUOTE]

It doesn't work in breezy. Something is broken but i can't find.
I want to know GNOME-way to disable beep because i'm using GNOME.

---

