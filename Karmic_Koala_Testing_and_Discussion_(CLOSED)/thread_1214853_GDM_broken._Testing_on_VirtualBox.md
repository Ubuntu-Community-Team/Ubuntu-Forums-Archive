---
title: "GDM broken. Testing on VirtualBox"
date: 2009-07-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-07-16
I'm testing Karmic in a virtual machine, and this broken GDM has left me with a black screen with a blinking cursor after the boot screen. I don't know if it's possible to switch to another tty with VirtualBox.

Any suggestions?

---

### Post by whoop on 2009-07-16
boot in recovery mode with networking... update the system and see if that helps. My install is fully updated and it works now, I had the problem yesterday...

---

### Post by aamukahvi on 2009-07-16
> **phenest said:**
> I'm testing Karmic in a virtual machine, and this broken GDM has left me with a black screen with a blinking cursor after the boot screen. I don't know if it's possible to switch to another tty with VirtualBox.

Any suggestions?
Use the Host key + F1

---

### Post by phenest on 2009-07-16
> **aamukahvi said:**
> Use the Host key + F1

Thanks for that.

Except now I have a kernel panic and can't do a thing with it. Maybe I'll start again.

---

### Post by Caseyjp on 2009-07-19
Had/have the same problem. solution was to host+f1 stop gdm (sudo /etc/init.d/gdm stop) restart it, then host+f7.

gmd greeter popped up and gfx fine.  happens every boot. (that and the stupid --nofloppy nonsense in grub)

---edit---

following today's updates, I no longer need to restart gdm.  Just host+f1 and then host+f7 back and gdm and graphics are fine.

It appears to be some sort of glitch with the virutalbox gfx driver.  

VBOX does appear to go unresponsive for about 20-30 seconds before a garbled screen shows up.  Then doing the f1 > f7 routine resolves it.)

---

### Post by aamukahvi on 2009-07-19
You should also try Virtualbox 3.0.2, it has video driver fixes among others. Works fine here.

---

### Post by jerrylamos on 2009-07-19
On the initial grub screen, edit the kernel line.
Remove splash. add nomodeset in place of splash.

nomodeset gets rid of KMS which has a bunch of birthing problems.

splash is causing some tty problems that didn't occur before.

That gets around a bunch of problems.  If it works you can play around example on one of my ati video graphics systems radeon.modeset=1 works, on the other it doesn't, I get a rainbow screen.

On two systems the driver vesa is distinctly faster than the latest 32 bit driver with the "accelerations" for KMS.  Read that "decelerations" on my pc's.

Jerry

---

