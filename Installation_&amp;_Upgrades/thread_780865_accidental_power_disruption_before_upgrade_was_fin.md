---
title: "accidental power disruption before upgrade was finished"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by karstruck on 2008-05-03
My upgrade to 8.04 was nearly complete when I lost power to the computer.  When I tried starting back up I get to the sign on and password screen, then nothing after that.  Plain orange screen and a cursor that can do nothing.
...help?

---

### Post by CREEPING DEATH on 2008-05-03
Oh boy that might be messed up.... try this:
Start it up until you get to GDM
Press CTRL+ALT+F4
This should take you to tty4
Log in with the same administrative user name you normally use.
Then, one at a time, waiting for it to finish:```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```
Then CTRL+ALT+F7 to return to GDM.  Try logging in and see what happens.  If it doesn't work, return to tty4 and ```
sudo init 6
``` to reboot it to see if it works now.
Beyond that, I can't help you much, Ubuntu runs like Ubuntu and has forked a bit from Debian.
You can check your sources.list from tty4 by:```
sudo nano /etc/apt/sources.list
``` CTRL+X to get out of it after viewing.
Good luck!

CD

---

