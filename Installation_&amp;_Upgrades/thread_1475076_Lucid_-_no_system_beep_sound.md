---
title: "Lucid - no system beep sound"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by hamhock on 2010-05-06
just installed Lucid 64-bit.  everything running smoothly including the sound except no system beep from PC speaker.  system beep is enabled in system -> preferences -> sound.  What else can I try?

I'm dual booting with Hardy and system beep works fine in Hardy.

---

### Post by hrstefanov on 2010-05-26
I guess ubuntu doesn't load the motherboard speaker by default. To load it type in terminal and when asked for password enter your user password:

sudo modprobe pcspkr

and check if it works

---

### Post by hamhock on 2010-05-27
> **hrstefanov said:**
> 

sudo modprobe pcspkr



tried - but no sound.

---

### Post by dino99 on 2010-05-27
install paprefs and gnome-alsamixer (tweak it into apps-sound-gnomealsamixer)

---

### Post by Joe Casadonte on 2010-06-14
> **dino99 said:**
> install paprefs and gnome-alsamixer (tweak it into apps-sound-gnomealsamixer)

I'm having similar problems and this does nothing for me.

PC Speaker worked fine for me under 9.10 (after much work, though: [http://ubuntuforums.org/showthread.php?t=1377990](http://ubuntuforums.org/showthread.php?t=1377990)), and now it's partially gone again.

This is really getting old.....

---

