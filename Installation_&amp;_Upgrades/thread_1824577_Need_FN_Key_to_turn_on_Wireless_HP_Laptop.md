---
title: "Need FN Key to turn on Wireless HP Laptop"
date: 2011-08-14
forum: Installation &amp; Upgrades
---

### Post by ohiamnotgoodwithcomputer on 2011-08-14
Hi guys!
A few days ago I got a new HP laptop (model number           dv7-6157cl), and my operating system wasn't able to recognize my wireless card (ralink 5390)

I downloaded the driver off of the ralink website, and successfully was able to install it (now when write the command "ifconfig" in my terminal, there's a paragraph about ra0), but my WiFi is still disabled. I think this is because I need to enable it using an "fn" key combination, but my laptop doesn't react to the combination to enable wifi.

If it would help, my laptop is brand new, so i don't mind formatting a partition if necessary, and i am willing to paste results of terminal commands if you need them

Thanks!

---

### Post by ohiamnotgoodwithcomputer on 2011-08-14
oh yeah, and if you couldn't have guessed, i'm not very experienced in messing with drivers/wireless cards 
(bump)

---

### Post by ohiamnotgoodwithcomputer on 2011-08-14
I recently booted into windows and was able to turn on wireless using the fn key
Rebooting back into ubuntu, the wireless card remembered to be on.
My problem now is of much less gravity, but i still would like to know how to make the fn key work, if anyone could give a few pointers

---

### Post by Mark Phelps on 2011-08-14
It's been a LONG time since I messed with this (so, the details might have changed) ... but one of the main reasons I had to remove Ubuntu from the laptop I used all the time is that Linux kernels newer than the ones that came with Hardy simply would NOT detect the special keys on my laptop anymore.

The OLD way of checking this was to run xkey -- which would open a small window on the desktop.  Then, with the mouse cursor positioned inside that window, you pressed a key -- watching for results in the window.  If the kernel detected the keypress, there was some text displayed -- and you could then use that text to setup that key in Ubuntu.  If no text was displayed (which was my case), there was nothing you could do.

Hopefully, this situation has improved over the years so that now, there is a better way of checking this.  But, until someone chimes in with the NEW way, you can try this and see what happens.

---

### Post by ohiamnotgoodwithcomputer on 2011-08-17
thanks so much man, i'll try it out and report back

---

### Post by valantis on 2011-08-17
Hi i believe that you can manage the keys from system management on keyboard but eny that you want to do you can make it with shortcuts (example ctrl alt f). For your wireless key to activate it does'nt mater if it is on or off (if it's just push buttonto activate  and not on, off power for the  wireless) linux can see the wireless card and you can config it.

---

