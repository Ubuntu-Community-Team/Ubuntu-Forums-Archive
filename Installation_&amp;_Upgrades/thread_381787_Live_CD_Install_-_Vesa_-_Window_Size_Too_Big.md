---
title: "Live CD Install - Vesa - Window Size Too Big"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by Fred Walker on 2007-03-11
Working to install Unbuntu (6.10). Have x86 system with ATI X300 PCIexpress card. Using info found in forum (title ="Installing X800 X700 X600 X500 X300 Ati Video Cards")... I am getting close.

Steps so far are:
1) Boot with Live CD
2) Select first menu option (with "install")
3) Boot process gets to screen saying "no device detected", where I can select "yes" to look at text output of issue, or "no". I select "no", then it shuts down "X" server, leaving me at a blank black screen. By hitting "control-alt-F2" I get to a system prompt.
4) I type "sudo nano /etc/X11/xorg.conf"
5) I edit the file, changing "ati" to "vesa" for driver.
6) I enter "startx"

This then boots up Ubuntu and I am at the main graphical UI. The "install Icon" is there, so I click on that. Now, **here is the problem**:

**The install window is taller than the screen size!** The "buttons" are below the bottom of the screen so I can not access them. The first screen is for selecting language. For that screen I can "guess" using "tab key" to select the right button to go to the next window. After that, the guessing is impossible.

I tried changing the font size, which helps some, but not enough to see the selection buttons. The windows are not designed to be shrunk (by dragging the corner of the window with the mouse), so that doesn't help.

My monitor is a LCD, 1280x1024.

There is probably some xorg.conf setting to change this behavior. Or ????

Any ideas?  Thanks!

---

### Post by Fred Walker on 2007-03-11
After more experimenting, I found that, at the initial boot screen main menu (from the Live CD) that at the bottom, one of the "F" keys would allow me to change the resolution. It normally says "VGA", but I changed it to 800x600x24. Now when I follow the above procedure the graphical UI comes up in 800x600 and I can now see all of the install windows and can access the buttons.

Looks like "this" issue is solved.

---

### Post by schatter on 2007-10-14
Hi - I have exactly the same problem.  Can you clarify, which window and which 'F' key(s) did the trick for you - i.e. allow you to change from 'VGA' to a different resolution?  Thanks.

---

### Post by TROJAN_COW on 2008-01-26
i found out the solution:
i had the same problem just go to system>preferences>keyboard shortcuts
then find the one that should be disabled click on it and press F1 to set that macro then go into your install screen and press F1 and that fixes it:guitar::lolflag:

---

