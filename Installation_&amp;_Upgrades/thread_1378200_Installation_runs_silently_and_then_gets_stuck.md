---
title: "Installation runs silently and then gets stuck"
date: 2010-01-11
forum: Installation &amp; Upgrades
---

### Post by dannyfel on 2010-01-11
I tried installing Ubuntu 9.10 using both Ubuntu Desktop CD and the Netbook Remix on a EEEPC 1005HA with an external CD drive.

In both cases I don't get any graphical interface during the installation. The CD is apparently installing everything silently, without letting me change anything on the way, and then it gets stuck.

The only screen I get is the first one, with the options to "try Ubuntu" or "install Ubuntu".

What's going on?

---

### Post by fluffen on 2010-01-11
I had this problem to, my screen goes black after i hit "Installation".
The solution for me was to add
 ```
i915.modeset=0
``` in the command line, to do this press F6 then escape and add the code.

Edit;
If the above works for you. You should add the command in /boot/grub/menu.lst. In the first entry add **i915.modeset=0** next to the vga bit and save the file :)

---

### Post by dannyfel on 2010-01-11
This solution didn't work. Same results.

---

### Post by dannyfel on 2010-01-11
By the way, just tried it with 9.04... and it works. I get the normal installation step-by-step screens. What's wrong with 9.10?

---

### Post by dannyfel on 2010-01-12
I figured out what was going on:

Although I asked for "Install Ubuntu", the CD decided to run "Try Ubuntu" instead.

After about 15 minutes of blank screen, I got the Desktop with user Ubuntu logged in, and then I could run the "Install Ubuntu" from the CD which appeared on the desktop.

I assume it's a bug, right?

---

