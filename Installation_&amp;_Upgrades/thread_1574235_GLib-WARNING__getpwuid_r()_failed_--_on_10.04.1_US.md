---
title: "GLib-WARNING **: getpwuid_r(): failed -- on 10.04.1 USB boot"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by DrJohn999 on 2010-09-14
On an ASUS M3N78-EM board (2 G RAM, built-in NVidia grahpics) attempting to boot off a 4-GB USB drive created on another Lucid machine with the 10.04.1 x386 or AMDx64 Desktop iso, I get the (now familiar to some) error: ```
GLib-WARNING **: getpwuid_r(): failed due to unknown user id (0)
```
I can boot into the installer by pressing the 'a' key as the initial line of text appears, before Plymouth starts. From there F6 and set ACPI=OFF and choose either "try" or "install". When the Plymouth screen (purple with Ubuntu and red dots shifting every second) comes up again press Esc to drop out and see the text messages. Then the rest of the startup runs through and the installer starts.
After the intial install the system boots up just fine. I'll post again if I encounter this error post installation. 
Note that this error did not occur with 10.10-beta x64 on the same machine.

---

### Post by pier56 on 2011-03-19
Thanks a lot, worked for me.

---

