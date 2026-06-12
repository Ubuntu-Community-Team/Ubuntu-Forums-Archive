---
title: "Failed to start the X server - Unable to access command prompt"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by itchypup on 2007-04-17
I have been successfully running Edgy on my Dell Inspiron e1705 for several weeks now.  I had some trouble setting up my Intel 945gm integrated graphics, but after installing the 915resolution package, everything worked fine.

I recently tried to install Feisty off of the Live CD, and it booted to the familiar "Failed to start the X server" error.  When installing Edgy, I was able to clear these errors, then Ctrl-Alt-F2 to a command prompt.  This is NOT working in Feisty, as after clearing the X Server errors, I am simply brought to a blank screen with no command prompt.

Ctrl-Alt-F2 will not bring up a command prompt.

Help me!  I want feisty too!

---

### Post by zvacet on 2007-04-17
Boot in recovery mode,and you will be root.
```
dpkg-reconfigure xserver-xorg
```

To see and correct if something is wrong.After that
```
/etc/init.d/gdm start
```

---

### Post by cyrusdh on 2007-04-17
How do you boot into recovery mode?  I am guessing you go through the f6 option but what is the command from the boot prompt?

---

