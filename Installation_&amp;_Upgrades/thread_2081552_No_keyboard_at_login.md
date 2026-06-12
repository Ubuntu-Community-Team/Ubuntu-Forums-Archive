---
title: "No keyboard at login"
date: 2012-11-07
forum: Installation &amp; Upgrades
---

### Post by nnahler on 2012-11-07
After booting I am presented with the login screen (Ubuntu 11.10 64 bit, Kernel 2.6.38-16). The mouse is working but keyboard is not.

It does not take any inputs on the password prompt. It also does not take any inputs from the onscreen keyboard if I activate it.

The keyboard works at Grub level, in Windows 7 (dual boot) and when I just boot into a root shell. I also tried booting into previous kernel versions without success (2.6.38-14).

To me it does not seem to be a keyboard or a kernel problem but rather a problem with the login screen.

This is a Dell Inspiron 13 laptop.

---

### Post by 2F4U on 2012-11-07
What happens if you disconnect and then reconnect the keyboard?

---

### Post by nnahler on 2012-11-07
It is a laptop. The keyboard (hardware) works. The login screen does not take any key inputs, also not from the onscreen keyboard using mouse clicks.

---

### Post by nnahler on 2012-11-25
The solution can be found here:

[http://www.techsmartlife.com/2011/10/13/keyboard-not-working-in-ubuntu-login-screen/]("http://www.techsmartlife.com/2011/10/13/keyboard-not-working-in-ubuntu-login-screen/")

Summary: In the bottom right corner of the login screen start 'Universal Access Preferences' (the human in a circle symbol). Deselect the last item: 'Press and hold keys to accept them (Slow keys)'

I have no idea why/how this box in the 'Universal Access' was ticked on my machine.

---

