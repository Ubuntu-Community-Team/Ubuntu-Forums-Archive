---
title: "Ubuntu won't boot after update"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Liath on 2008-02-18
After a bit of work I finally got around to installing 7.10
After I got logged on the first thing I did was to update so clicked the little update thing and updated everything

Then when it got to the point where it says it's installing software and about 80% done the screen changes to a blue one with text telling me something about "x-server is already running...." and then a yes no prompt but before I can read it I get a kernel panic

After I restart I get to the login screen and login but afterwards all I get is a gray or orange screen with the mouse cursor that I can move but nothing else happens

Please any help would be appreciated

Dell Dimension e520
Intel Core 2 Duo 1.86Ghz 2M cache
160GB Main HD
5gig Ram
Radeon x1300 pro

---

### Post by kaiju on 2008-02-18
i am not sure about this because of the weird x server thing.
however, if you have access to any of the terminals (ctrl+alt+f1 to f6, and ctrl+alt+f7 to get back to the gui), you could try running the upgrade again by entering
```
sudo apt-get upgrade
```
even if this won't fix it, you might get some useful error messages.

---

### Post by Partyboi2 on 2008-02-18
when you get to the login screen instead of login in press ctrl+alt+f2 to get to a terminal and login there. Then try reconfiguring xserver.
```
sudo dpkg-reconfigure xserver-xorg
``` choosing the default answers if unsure.

---

