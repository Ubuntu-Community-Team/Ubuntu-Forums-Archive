---
title: "Odd mouse/kb pausing"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by ericsonp on 2006-06-20
Just upgraded from 5.10 to 6.06. Now both mouse and keyboard inputs often hang indefinitely until the mouse is moved. Then the most recent mouse or keyboard input is processed. For example, when I type "uname -a" nothing appears in the term until I move the mouse, then it shows up and executes.

uname -a shows:
Linux paule2 2.6.15-25-686 #1 SMP PREEMPT Wed Jun 14 11:34:19 UTC 2006 i686 GNU/Linux

---

### Post by sgbeamer on 2006-06-20
I'm having similar issues with the newer kernel.  If you upgraded try the Breezy kernel and see if this solves your problem.   You might also go to a terminal window Alt-F1 and see if you are getting a USB reset issue.  I am getting a message like:

usb 5-8 not accepting address 3, error -110

---

### Post by ericsonp on 2006-06-21
With more testing I've discovered the following:

-The mouse click seems to start the problem.
-Gnome animations also seem to be slowed down, such as when an app is launched from the Panel.
-The 2.6.15-25-386 kernel image from the dapper build works fine so it's a problem with the 686 kernel image.
-I've also not been able to re-install the Synaptics touchpad drivers since re-running the Xorg setup. Tried both :
  -xfree86-driver-synaptics - Synaptics TouchPad driver for X.Org/XFree86 server
  -xserver-xorg-input-synaptics - Synaptics TouchPad driver for X.Org server
But qsynaptics will no longer recognize either driver.

I suspect the problem is related to a conflict between the 2.6.15-25-686 kernel config and the synaptics driver.

---

