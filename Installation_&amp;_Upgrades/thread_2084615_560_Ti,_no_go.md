---
title: "560 Ti, no go?"
date: 2012-11-15
forum: Installation &amp; Upgrades
---

### Post by quenturi on 2012-11-15
Installed, from a USB stick, a fresh new ubuntu 12.10 64 bits on a dedicated hd. Mobo is a GA-X58A-UD3R (latest bios FH) running 12 Gb with a i7 950 and a GV-N560OC-1GI (latest bios as well).

During the installation, I noticed some text and some icons were like scratched. Once the install process was finished, I logged in and didn't notice anything wrong but when I started to run the ubuntu app to install new apps, the very same problem popped up again: some text and some grahics like washed up or scratched. So I guess it's obviously some graphic issue. Anyway, I tried to install nvidia current drivers (304 something) and restarted the system. Now, I can log in (with LightDM using the wrong res unlike the default driver at first) and then... all I got is an empty desktop with the wallpaper and nothing else. Had to use CTRL-ALT-DEL to exit that depressing desert. During reboot I can see briefly the tty is huge (very low rez).

It's a mess with or without nvidia drivers which is kinda new. On that computer, I ran 11.10, 12.04 just fine (with and without nvidia current drivers). 12.10 is a big fail for me.

BTW it works fine on Windows 7 64.

Reinstalled twice, same symptoms.

Checked the sticky post about graphic problems but I have none of the problems mentionned :

- Error- "Cannot display this grahics mode": Have no error message at all
- GRUB_GXFMODE-auto results in Blank screen problems on Startup? (this includes purple or black screen, flashing cursor, stuck at splash screen...): no purple or black screen, no flashing cursor, not stuck at splash screen
- No Grub Menu?: I do have a GRUB menu

Any suggestion?

Thx

---

### Post by Mr_JMM on 2012-11-15
Yes - 
See if there's a (linux) driver you can download for your card from the Nvidia website.
Use 12.04.

---

