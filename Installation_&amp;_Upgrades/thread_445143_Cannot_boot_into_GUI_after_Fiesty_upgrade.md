---
title: "Cannot boot into GUI after Fiesty upgrade"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by Killerfocus on 2007-05-15
Hey guys, 
I just want to start off by saying in advance thanx for any help you guys give and i apologize if this is a dupe.
I recently upgraded to Fiesty Fawn on my desktop.  The upgrade completed without any errors.  For some reason, when i try to boot into ubuntu, after the initial Loading screen with the orange progress bar, the screen turns blank and there is no GUI.

---

### Post by spd106 on 2007-05-16
Have you tried pressing Alt-F4 or booted via the recovery option?

What kind of graphics card do you have?

If you can get to a terminal prompt and log in, then try running this command to regenerate your xserver's configuration file.
```
sudo dpkg-reconfigure xserver-xorg
```

---

