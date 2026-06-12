---
title: "Acer 212T and Ubuntu"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by kwomki on 2007-02-25
Good evening.

I have an old Acer TravelMate 212T laptop that I fancy trying Ubuntu on.

Spec:

Celeron 800Mhz Processor
12.1" TFT (XGA)Display
64Mb RAM
10Gb Hard Drive
Internal CD-Rom Drive
Internal 3.5" Floppy Disc Drive
Internal 56K V90 Modem
4Mb SGRAM(Video Memory)
2X ATI Rage Mobility-M1 Graphics Accelerator

When I try to install Ubuntu I get passed the part which says Ubuntu 6.10 with the orange bar that moves from left to right indicating that it is preparing to install and then the screen goes black except for a white cursor/line flashing at the top.

I have searched the forums to see if anyone has had similar problems but to no avail.

Please help

kwomki

---

### Post by nyinge on 2007-02-25
Is this when you're booting with the Live CD?  When you see the orange bar, press Alt+F1 and see what the output are.

I'm sure it will take a long time to boot up the Live CD considering the amount of RAM on the Acer.  I'm talking at least several min here.  :)  Do you see your hardrive light flashing while the cursor is blinking?

---

### Post by jjrr on 2007-02-26
hmm, i just wanted to install on a similarily low-end notebook (128 mb ram, pIII 600) and it failed with "no space left on device". i thought maybe i had to tell it about using a swap partition on  the boot prompt but i didn't remember of figure how to do it. is it even necessary? 
btw. are there also ncurses based (or sth. alike) ubuntu installers?

---

### Post by kwomki on 2007-02-26
> **nyinge said:**
> Is this when you're booting with the Live CD?  When you see the orange bar, press Alt+F1 and see what the output are.

The message I get is 

Calling INT 0x1A (F000:FE6E)
  EAX is 0xB102
Calling INT 0x1A (F000:FE6E)
  EAX is 0xB10A
[17179586.032000] irq 15: nobody cared (try booting with "irqpoll" option)
[17179586.032000] handlers:
[17179586.032000] [<c02528e0>] (ide_intr+0x0/0x1f0)
[17179586.032000] Disabling IRQ #15

> **nyinge said:**
> Do you see your hardrive light flashing while the cursor is blinking?

Not whilst the cursor is blinking but when the orange bar is moving left to right the hardrive light is flashing.

---

### Post by nyinge on 2007-02-26
Did the cursor just blink and the screen stay dark forever?  Is it possible for you to try out Xubuntu instead?  I'm not an expert here, but I'm just trying out the possibilities.  Xubuntu is much lighter, and hopefully we would see a difference here.

---

### Post by nyinge on 2007-02-26
duplicate post.  sorry!

---

### Post by nyinge on 2007-02-26
I'd strongly encourage to try out Xubuntu first.  I don't think you'll need to turn on swap partition with 128 mb ram.  I had successfully installed Xubuntu on a 64MB of RAM box.  The installer did ask me to turn on the swap partition in the beginning, but it did it automatically.  It however took me about 15min just to load the Live CD.  The actually installation took forever lol.

---

### Post by kwomki on 2007-02-27
I shall try Xubuntu and get back to you with my progress.

Wish me luck.

---

### Post by nyinge on 2007-02-27
> **kwomki said:**
> I shall try Xubuntu and get back to you with my progress.

Wish me luck.
Good luck, kwomki.  May the force be with you!  :P

---

