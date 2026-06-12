---
title: "Start to command/shell prompt?"
date: 2007-02-18
forum: Installation &amp; Upgrades
---

### Post by vendejp on 2007-02-18
I hate to post this, but Ive been searching for an hour and cant find anything.
[B]
short story:[/B]
Is there a way I can start to the command/shell?  That is, without editing any conf files since I can't even get to them.  some button to hold down or something?

**long story:**
Ive installed 6.10 in text mode because my display has a resolution of 1680x1050 which results in "input device not found" when trying to install via graphics mode.  I expected the install to ask about my display, but it didnt.  Now, install is complete, however on startup I assume it starts X and I have the same problem where my display goes blank.

Maybe I should have chosen "Install a command-line system" but I do want X installed because I simply want to configure the x11 conf and try to get things going.  Trying to find out what the "command line system" is led to nothing.

Thanks in advance
Josh

---

### Post by taurus on 2007-02-18
<Ctrl><Alt>F2 should get you to a console where you can log in.  Then, reconfigure your X again with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by vendejp on 2007-02-18
Exactly what I was looking for!

Thanks so much

---

