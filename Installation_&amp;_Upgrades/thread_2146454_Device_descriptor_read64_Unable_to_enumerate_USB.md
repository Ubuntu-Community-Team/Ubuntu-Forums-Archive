---
title: "Device descriptor read/64 Unable to enumerate USB"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by ERRRIMMAD on 2013-05-18
I have run into some kind of strange problem.

I know this is not a hardware problem because I'm using the same hardware with a different hard drive, but the same kind of OS Ubuntu 12.04

What I did when the crash happened.

I installed Nvidia experimental driver 310

Everything worked but it was not something I needed, so I moved back to the recommended driver and restarted my system.

Then came the crash.

Device Descriptor read/64 error-71
Device not accepting address (XX) error -71         (xx) represents a number that changes every new line generated.
unable to enumerate USB device on port 2

This repeats for like three minutes before it locks up, and the screen goes to sleep.

If i hit the power button it will shut down the system

as it shuts down it will say something about halting virtualbox.

I might also point out I had a problem with WINE about three days earlier, I tried to install crazy taxi on wine and it crashed wine so when I logged back in it blocked out the whole desktop with grey, and the Ubuntu menu icon was unusable, I fixed that by running ALT +F2 and typing gksudo synaptic, removing Wine, purging the install after removal, and reinstalling, but I don't believe that to be the problem as everything seemed to be fine.

I was also able to get to grub by hitting **** at boot.

This is some messed up BS, is their any way for me to force my way back in, or to install the OS again without over writing my previous settings?

ERRRIMMAD, what to do, am I going to be forced to clean install to fix this nuisance, I cant even get to the OS to run terminal, see a log in screen, or anything because of the error loop that goes on and on at boot keeping me out of my OS.

---

### Post by Jonor on 2013-05-20
So just to clarify, you have two internal hard drives in one box, both with Ubuntu 12.04. Booting into one drive is fine, whereas the other gives a usb error before locking up and this is all reproducible behaviour ?

---

