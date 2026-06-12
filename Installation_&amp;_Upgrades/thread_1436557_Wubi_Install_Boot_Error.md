---
title: "Wubi Install Boot Error"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by Tonewah on 2010-03-22
I've just installed Ubuntu / Wubi on a Vista box. After restarting and selecting Ubunto to boot, then selecting Ubuntu again, I got the Ubunto symbol, like on my Ubuntu netbook.
 
Then I get this scrolling message:
 
intelfb_restore *error* failed to restore cftc configuration
 
I can alt-ctr-del to get into the recovery terminal boot, but I have no real idea what to do. I'm guessing it's a video issue, but I'm not sure.

---

### Post by Tonewah on 2010-03-23
I"ve tried the insertion of 'i915.modeset=0" into the boot dialog, inserting 'vga=xxx', where xxx=3 digit number, and neither of them have worked.  
 
The screen continues to flicker, and my monitor switches from mode to mode.
 
I've installed Ubuntu 9.10 via wubi, to clarify.  Any ideas?

---

### Post by Roby718 on 2010-03-23
The proper X Crash Command is 'Ctrl-Alt-Bksp.';)

---

### Post by Mark Phelps on 2010-03-24
Not at my Linux box, but from what I recall, Ctrl-Alt-Bkspace does NOT work in Ubuntu 9.10.

Did you install any video drivers?  Or did you start getting display problems immediately after install?

Suggest you boot from a LiveCD to at least see if you get video that way.

---

### Post by Tonewah on 2010-03-24
The error began immediately after the install.  Never made it into the GUI.  
 
Someone suggested eliminating the 'splash' screen, but I still had the same issue.  I can get to the term prompt.  Error occurs when I try to start the GUI.
 
When I add the 'i915.modeset=0' line, the error goes away, but the screen flickers and the monitor changes mode continually.
 
I tried the USB live boot, but had the same issue.  Haven't burned a live CD, though.
 
Thx for the help!. I love Ubuntu on my netbook, would love it even more on the desktop box.

---

### Post by Tonewah on 2010-03-25
I can now get the GUI to start, after downloading a newer kernel and adding 'nomodeset' to the boot commands.  After more googling, I believe the problem lies with my intel chipset 82945G.  I can't figure out how to change the resolution to anything other than 800x600, and the error text when the GUI starts up is so small, it's unintelligible.

---

