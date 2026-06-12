---
title: "Acer Laptop hangs after fresh install and first update"
date: 2010-06-12
forum: Installation &amp; Upgrades
---

### Post by shinkaide on 2010-06-12
I just installed 10.04 on an Acer 4736 laptop and was prompted for a software update of about 170 MB. 

I went through with the update downloads and installation, got an error message of some packages not being found, and clicked on the "close" button on the dialogue to finish with the whole thing. 

Now the Update Manager window with the grayed-out package updates didn't go away, and the cursor would always show the "busy" circle thing. I waited for a while, but nothing happened. I tried opening Firefox to check for anything about this on the net, but it wouldn't open. 

So I left it alone, and it the screen went black (screensaver, I guess). When I tried to get back to the desktop, I couldn't. Screen wouldn't respond and it stayed black; no password prompt or anything.

Ctrl-Alt-Backspace wouldn't take me back to the login screen either.

Help, please?

---

### Post by mtrausch on 2010-06-12
Try rebooting the system (Control+Alt+F1 should bring up a virtual terminal and then you can reboot with Control+Alt+Delete; if that doesn't work, try holding down left Alt+SysRq and press the following keys in sequence: R S B; if that doesn't work, press the reset button on the case).

When the system comes back up, login and try the command "sudo apt-get -f install".  If you have issues with that, post back and we'll see what happens from there...

---

### Post by shinkaide on 2010-06-13
Hey, thanks a lot - that's just what did the trick! Took a while after the key presses before the laptop responded, but I was able to reboot the laptop, and everything went fine.

I ran "sudo dpkg --configure -a" to fix the stuff that didn't get done right during the hang. 

Thanks again!

---

### Post by mtrausch on 2010-06-14
Excellent!

Glad to have helped.

---

