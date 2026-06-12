---
title: "Lucid Flashes. CRTC 64 error?"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by jasex on 2010-03-20
after upgrading via command line to Lucid, on my acer aspire 1410 the screen flashes, I think it may have something to do with X

but not sure. It gets really slow as if it is a graphics card problem and the flashing can only be resolved by switching to the terminl and back to x again, and then once more after logging in. it is not as bad if I disable compiz... 

My graphics crd is an intel 4500mhd which is obviously a shared card being a netbook range computer, and I can't remember how to edit xorg anymore, to test to see if the same issue occurs using the VESA driver...

it reports upon switching off compiz, or turning it on, tht the monitor cannot switch to crtc 64 

Some insight would be wonderful as to what I can do to discover the error cusing all this and submit a bug bout it so it will help out some other people.

---

### Post by DBO on 2010-03-20
Can you give more info about these "flashes". I may be experiencing the same thing.

---

### Post by yelvington on 2010-03-21
I am definitely seeing the same thing. 

Fortunately, I'm just testing it from a thumb drive. Xorg is consuming ~67% of CPU on a dual-core Intel Celeron SU2300. Anything that requires a screen redraw causes the "flashing" effect, and it begins with the selector that lets you choose to run/test or install Ubuntu, so it's not related to running the full Nautilus/Gnome environment.

I've been running Karmic on this Acer 1410 since the day I got it, and it's sweet.

If there is a ticket on this, I'd be happy to add observations.

---

### Post by yelvington on 2010-03-21
I have filed a bug report:

[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/543808](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/543808)

---

