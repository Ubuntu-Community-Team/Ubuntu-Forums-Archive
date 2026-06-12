---
title: "boot loads arrow pointer and nothing else (Clean install - 9.10)"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by gspat on 2009-12-10
Something interesting happening here...

Clean install on Acer Aspire T135 desktop with ATI HD 3650.

I tried using the standard live cd and managed to boot to a desktop but the install hung (waited 4 hours.. it really stalled)

I then downloaded the alt-installer and installed using that, but it booted to a blank screen with a movable arrow pointer. I can use crtl-alt-f1 to get to a tty and login.

I did the sudo alt-get update && sudo alt-get upgrade && sudo alt-get dist-upgrade and now have the newest kernal, but the display still does the same thing.

exploring around, I found that my home folder does not have the Desktop folder (or any folder at all) all it has is the examples.desktop file.

using service gdm stop works, but service gdm start freezes the system with a partial display of the graphical login screen. (brown background with black box where login should be).

stuck at what I should try next... help please?

---

### Post by gspat on 2009-12-10
solved it!

needed to download the ati driver from their website...

then chmod 777 filename.run

then make sure gdm isn't running (either by stopping gdm or using recovery off CD).

then sudo ./flename/run to install the driver.

finally, sudo aticonfig --initial to set it up

reboot and enjoy!

---

