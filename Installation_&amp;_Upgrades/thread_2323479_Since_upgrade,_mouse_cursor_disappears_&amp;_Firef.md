---
title: "Since upgrade, mouse cursor disappears &amp; Firefox doesn't scroll right"
date: 2016-05-05
forum: Installation &amp; Upgrades
---

### Post by peyre on 2016-05-05
I'm running 32-bit Xubuntu.  When I upgraded from 15.10 to 16.04, a couple behaviors got screwed up and I'm not sure what to do about them.

Whenever I lock the computer, when I unlock it, the mouse cursor disappears.  I can bring it back by opening a terminal window and running sudo service lightdm restart, but that closes everything I have running and I have to log in again.  Reinstalling lightdm doesn't seem to have helped.

Firefox isn't scrolling properly.  Instead of scrolling up or down a page when I click above or below the scroll blob, it jumps to wherever in the scroll bar the cursor is positioned.  It's become really annoying.  Other programs that weren't doing it before (e.g., Chromium) aren't doing it now.  Any suggestions?  I've toggled Smooth Scrolling and Autoscrolling on and off to no effect, emptied my cache and cleared cookies, still nothing.

---

### Post by Dennis N on 2016-05-05
This thread should help with the Firefox scrolling:

[http://ubuntuforums.org/showthread.php?t=2323003](http://ubuntuforums.org/showthread.php?t=2323003)

---

### Post by Dennis N on 2016-05-05
> **peyre said:**
> Whenever I lock the computer, when I unlock it, the mouse cursor disappears...

For this problem, try Ctrl+Alt+F1 followed by Ctrl+Alt+F7.

---

### Post by peyre on 2016-05-05
Dennis, your solution for Firefox worked like a charm!

The mouse cursor thing didn't, though.

---

### Post by Dennis N on 2016-05-05
Well, I can't take any credit for the Firefox solution. I think that is vasa1's suggestion on the other thread. I wasn't sure about the other "try it" suggestion; I neglected to write down the source - I read that someplace a few weeks ago and just make a note. 

You are not the only one to encounter this disappearing cursor after the screen is locked. There is a bug report on that against the Intel graphics system:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1568604)

EDIT: In fact, this bug report IS the source of my suggestion. See post #53 on the bug report.

---

