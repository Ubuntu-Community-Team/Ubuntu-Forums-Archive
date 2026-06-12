---
title: "Right Alt key not working"
date: 2009-09-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by FuturePilot on 2009-09-28
My right Alt key doesn't seem to be working. Right Alt+F2 does nothing, but left Alt+F2 works. I used to be able to switch channels in Irssi using the right Alt key but now it does nothing. Anyone else have this problem?

---

### Post by FuturePilot on 2009-09-28
Ok, well I found what the problem is, but I'm not sure how to fix it. Under the keyboard layout options, Right Alt is selected under "Key to Choose Third Level". When I uncheck it, it won't stay unchecked. The next time I open the layout options, it's selected again. In Jaunty, there is nothing selected under this category. I'm not sure why it's has something selected by default.:confused:

---

### Post by krazyd on 2009-10-09
Just thought I'd post a fix to this problem. For some reason, X set my keyboard's right alt key to level3 mod switch. To fix this and restore normal alt mapping, open up this file in your favourite editor:
```
/etc/default/console-setup
```
Comment out this line by adding a '#' at the start. (the line is probably somewhere near the bottom of the file):
```
XKBOPTIONS="lv3:ralt_switch"
```

Restart X, or just reboot for the change to take effect.

Hope this helps someone! :D

---

### Post by FuturePilot on 2009-10-09
Thanks! That fixed it. I had to reboot though, restarting X didn't seem to be enough. My theory is that it might be a bug with the alternate installer. I installed Karmic on another system using the live CD and it didn't have this problem. I'll have to do some testing, but I think that might be the case.

---

### Post by bhrgunatha on 2009-10-26
I have exactly the same problem - and I also installed using the alternative CD.

---

### Post by FuturePilot on 2009-10-26
Here's the bug report. I've added the debian-installer to it. [https://bugs.launchpad.net/debian-installer/+bug/438520]("https://bugs.launchpad.net/debian-installer/+bug/438520")

---

