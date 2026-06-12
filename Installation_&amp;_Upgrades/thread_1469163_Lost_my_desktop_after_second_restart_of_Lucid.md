---
title: "Lost my desktop after second restart of Lucid"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by mathias j sagartz on 2010-05-01
Working with an old desktop that had been running 8.04

Update failed so I installed from a LiveCD.  Dual boot with XP.
System runs great off of the CD.  After installation of 10.04 and
a restart, the system worked well.  Tried lots of stuff off the Gnome menus.

Restarted and booted XP.  That worked too.

On my next restart I selected Ubuntu from the grub menu and the system gave me the sign in requester.  I signed in but the desktop never appeared.  All I got was the background and a mouse pointer.

Right clicking the mouse brings up a 7 item menu that includes items for creating a folder, creating a file, ....., choose a new background.  The menu works.  If I click create a file an icon for a new file appears on the screen.  Clicking on the icon brings up a window running gedit.  Choosing the new background item brings up a window with candidate new backgrounds.  I have no idea how to get the gnome desktop back.  The sign in screen has a bar at the bottom that shows Gnome is the default session setting.

Booting into XP continues to work.

I've tried changing the GRUB_CMDLINE_LINUX_DEFAULT= line in the /etc/default/grub to add nomodeset.  That didn't help.

---

### Post by Propwash on 2010-05-05
I have the same problem.  The screen boots up and... no menu.  I can do the same thing and right click the mouse to get the pop up.  If I find a solution I'll post.

---

### Post by tubunu on 2010-05-05
```
startx
```

---

