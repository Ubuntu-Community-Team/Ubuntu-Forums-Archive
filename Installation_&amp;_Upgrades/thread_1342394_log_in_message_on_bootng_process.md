---
title: "log in message on bootng process"
date: 2009-11-30
forum: Installation &amp; Upgrades
---

### Post by grc01 on 2009-11-30
I had upgrade  to 9.10 3with success. While removing a program (game) my pc restarted but did not boot successfully. The screen shows Ubuntu 9.10 laptop tty1
laptop log in:
I have try too reboot with my old cd no luck.
How can i reboot? thanks

---

### Post by lemming465 on 2009-12-01
If you are getting the "...tty1" prompt you are at a "text console" or "virtual terminal", probably because X windows isn't starting correctly.  Command line wizards can switch between X and VTY using Ctrl-Alt-F1 and Alt-F7 if they are in the mood.  The first repair strategy I'd try is to login at the text console with your normal username and password, then maybe```

sudo -i
aptitude clean
aptitude update
aptitude full-upgrade -f
dpkg-reconfigure xserver-xorg
reboot
```
The sudo goes into a root shell.  The aptitude clean & update clear your cached .deb package downloads and refresh your lists of current packages.  The "aptitude fullupgrade -f" tries to download and install any new bug fixes, including reconfiguring any packages currently marked as only partially installed.  The explicit reconfiguration of the X server is the first way to try getting that back.

---

