---
title: "Can't boot install CD on Intel CA810e"
date: 2006-07-30
forum: Installation &amp; Upgrades
---

### Post by tjfs on 2006-07-30
Can't boot the live CD on this system. Works fine on my laptop so the CD is OK. Previous version of Ubuntu (5.x) wouldn't boot on this system either. Runs XP fine. 256MB RAM + Celeron 900MHz CPU.

---

### Post by rowanparker on 2006-07-30
Is your BIOS set to boot from CD?

---

### Post by tjfs on 2006-07-30
Yes; it gets some way into the boot process and then hangs.

---

### Post by rowanparker on 2006-07-30
At what process does it hang on? What is on the screen?

---

### Post by tjfs on 2006-07-30
Gets as far as _ in the top left corner.

I wonder.. I've got two video cards, could this be the problem?

---

### Post by tjfs on 2006-07-30
I tried the safe graphics boot and it stops at a shell prompt. Tried xinit and it said it couldn't understand either of my video cards, so I guess that's the problem. 

The normal boot dies just after Starting Gnome Display Manager.

The CA810e has onboard Intel graphics and I also have a PCI video card installed - it's a Riva TNT 16MB.

---

### Post by rowanparker on 2006-07-30
Which video card is your moniter plugged into? Have you tried both?

---

### Post by tjfs on 2006-07-30
The BIOS automatically uses the PCI video card in preference to the onboard video, the monitor is plugged into the PCI card. I did try moving it to the onboard VGA socket, no signal present. I think it's significant that when I do a safe boot and try and run xinit I get the message saying that neither video card is recognised.

---

### Post by rowanparker on 2006-07-30
Sorry, I'm lost.

Has anyone else got any ideas?

---

