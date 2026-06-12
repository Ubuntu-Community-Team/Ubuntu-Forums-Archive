---
title: "No boot/shutdown progress, login screen off centre"
date: 2008-08-19
forum: Installation &amp; Upgrades
---

### Post by roncrump on 2008-08-19
I've just installed Hardy on a work machine. Two little problems:

(1) When booting I am not getting any progress graphics (the Ubuntu logo and orange progress bar), this is also occurring during shutdown.

(2) After my installation, I manually set the monitor to be the one actually being used. Previously it had made a guess and part of the screen was not being used. Anyway, once I am logged in everything is fine but before login, the login has the Ubuntu logo off-centre and the options at the bottom off of the screen, as if the "desktop" being created is too big for the screen.

Suggestions?

Thanks,
Ron.

---

### Post by Partyboi2 on 2008-08-19
Check your Usplash configuration file to make sure it is correct.
```
gksudo gedit /etc/usplash.conf
```if it shows something like this
```
# Usplash configuration file
xres=1280
yres=1024

```make sure that the numbers are what your screen resolution uses. So for example if your screen resolution was 1024x768 it would look like this:
```
xres=1024
yres=768
```If you make changes after saving the changes type
```
sudo update-initramfs -u
``` to update.

---

### Post by roncrump on 2008-08-19
Thanks for the suggestion.

My /etc/usplash.conf file had the correct resolution, but I tried the
```
sudo update-initramfs -u
```
command anyway. No difference, still off-centre/over-sized login screen and no boot/shutdown progress info.

Ron.

---

### Post by roncrump on 2008-08-20
I tried installing startup-manager in order that I could try tweaking bits and pieces. Anyway, having set the resolution to be 1280x1024 (right for my display) in there and trying to reboot, I get a message that I have an invalid video mode. I think this confirms that there is some incompatibility between the display and PC hardware. Which is quite possible - the monitor was added last year when there was a nice 19" one going spare in the department. I guess the operating systems help the monitor and PC to work properly together once they are booted.

So I guess I shouldn't worry too much about this fairly minor problem.

---

