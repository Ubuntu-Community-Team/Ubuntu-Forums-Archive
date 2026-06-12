---
title: "Installing Ubuntu Desktop on my Inspiron 1300 ....."
date: 2007-03-23
forum: Installation &amp; Upgrades
---

### Post by jimbobsquarepants on 2007-03-23
I'm very new to the whole Linux thing .... last nite i decided to backup my laptop and wipe it. I downloaded myself a copy of Ubuntu 6.10, my laptop will boot into the live verison, it will install fine, but when it reboots, the Ubuntu loading bar will appear and after that the screen goes blank.

I've tried reinstalling it over and over again, i've downloaded the Ubuntu image from a couple of places, but still the same problem.

I've seen afew posts about Ubuntu on Inspiron 1300s ... but couldnt see anything about fixing the problem.

Does anyone know how to get it running on my laptop?

Cheers,

Jim :confused:

---

### Post by upbeat.linux on 2007-03-23
If there are no pretty flashing lights on your laptop and its still running then this sounds like a problem with Gnome.  Reboot and wait for the screen to go blank and then hit "Ctrl+Alt+f"

If you can login, do so now. At the prompt type: 

> startx

Do you get any error messages?  If you receive a fatal server error message there may be an issue with Xserver lock files. Visit your tmp directory and check for .X0-lock.

If it exists remove it:

> sudo rm -rf .X0-lock

Then try running startx again.

---

### Post by jimbobsquarepants on 2007-03-23
Hi, just tried that... when the screen goes blank nothing works

If i try pressing the caps lock button ... the light doesnt even come on.

Am i installing Ubuntu wrong or something?

Cheers

---

### Post by jimbobsquarepants on 2007-03-26
Dont worry guys i'll just go back to using Windows .... cheers anyway :(

---

### Post by ubuntnewb on 2007-03-26
If you decide to try again you should try hooking up an external monitor to setup your machine. I was able to finally get installed on my laptop by hooking up an external monitor, installing, updating, rebooting, and then I was able to unhook the monitor and use the laptop's LCD from that point on. I'm sure someone with a bit more experience could have done it all without the external monitor, but I'm lost without a GUI.

---

