---
title: "Unable to start for the first time"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by gavos on 2007-10-31
Hello guys,
I instaled the Feisty Fawn in 2 pcs today.. In the second one, the whole process was done ok, but when it tried to start for the first time Ubuntu almost stacked after the progress bar completed.. The progress bar takes 2 minutes to full, and after that i see the mouse pointer and nothing else (note that the refresh rate of the mouse pointer when im moving the mouse is every second!!!).. Its a Pentium 4 with Windows XP installed on the same 20gb disk, Ubuntu takes 5,5gb and 0.5gb swap.. Same things done to the other pc with more disk space and swap space with no problem.. Any ideas?

---

### Post by dabl on 2007-10-31
> **gavos said:**
> Hello guys,
I instaled the Feisty Fawn in 2 pcs today.. In the second one, the whole process was done ok, but when it tried to start for the first time Ubuntu almost stacked after the progress bar completed.. The progress bar takes 2 minutes to full, and after that i see the mouse pointer and nothing else (note that the refresh rate of the mouse pointer when im moving the mouse is every second!!!).. Its a Pentium 4 with Windows XP installed on the same 20gb disk, Ubuntu takes 5,5gb and 0.5gb swap.. Same things done to the other pc with more disk space and swap space with no problem.. Any ideas?

Sounds like video trouble, to me.  I would configure a VESA display, for starters, and then see if there is a better display driver available.  Probably you can do Alt-F1 or Ctrl-Alt-F1, or else boot to Recovery Mode, then

```
sudo dpkg-reconfigure xserver-xorg
```

on the first question choose "NO" to autodetect, and the second one choose "VESA", and then take defaults.  When finished, run ```
startx
```

:)

---

