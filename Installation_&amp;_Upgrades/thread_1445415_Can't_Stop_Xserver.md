---
title: "Can't Stop Xserver"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by SkilletHead on 2010-04-02
I am switching my main desktop to 9.10, installed on a new main hard drive, dual booting with XP already installed, which I switched to second hard drive. I installed from a live copy on a thumb drive made from the latest .iso downloaded from the Ubuntu website. The machine is a few years old, a 2.4 ghz dual core Pentium 4 with hyperthreading. I am not convinced that this is a hardware issue, but if you need to know what graphics cards I have and whatnot, I am glad to look it up. I do not have internet at the new house yet, so I have not updated the system yet. I have previous experience with Ubuntu running a server with the shell.

The first thing that I have to do before anything else is getting my three monitor setup working. Without that, I will not use Ubuntu, so it is no use installing everything else before I resolve this issue. I am certain that once I resolve this issue, I can get xinerama working correctly.

I am unable to stop the Xserver, so I can't create a xorg.conf file, because "Xorg -configure" requires Xserver to be stopped. These are the methods I have tried: (all in the command prompt accessed by CTRL-ALT-F1)
sudo /etc/init.d/gdm stop
Resulted in a message "Rather than invoking init scripts through /etc/init.d, use the service(8) utility, eg.g service dgm stop (line break) Since the script your are attempting to invoke has been converted to an upstart job, you may also use the stop(8) utility, e.g. stop gdm"

So, I tried
sudo stop gdm
Resulted in "Warning: Fake initctl called, doing nothing."

So, I tried
sudo service gdm stop
Resulted in "Warning: Fake initctl called, doing nothing."

I also tried CTRL-ALT-Backspace, but that had no effect.

I've been doing research for two hours and no luck.

What else can I try?
What does "Fake initctl called" mean?

---

### Post by Shazaam on 2010-04-02
Round-about way that works for me...
1. At the grub boot screen choose "Recovery mode", log in.
2. When you get to the choices list choose "Drop to a shell" (or similar)
3. Enter...
```
sudo service gdm stop
```
4. Carry on from there.

CTRL-ALT-BACKSPACE is disabled by default. Go to System>Preferences>Keyboard>Layouts>Layout Options button>Key sequence to kill the X server, check the box.

---

### Post by SkilletHead on 2010-04-03
Thanks for your help. I should have thought of the terminal on recovery mode. 

I got the multiple monitors working using RandR. It looks it would be more seamless with a quad head video card, (it runs one xserver per card) but its working!

---

