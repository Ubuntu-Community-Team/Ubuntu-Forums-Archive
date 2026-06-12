---
title: "Ubuntu 12.04 livecd won'd boot"
date: 2012-06-02
forum: Installation &amp; Upgrades
---

### Post by erith2000 on 2012-06-02
I just built a new computer and am attempting to install ubuntu 64 bit on it.  I am able to get to the purple try ubuntu/install ubuntu/check disc to defects/... screen, but nothing I have tried will get me past there.  It hangs on a black screen with a flashing cursor.

I had installed an nvidia 550 ti video card, but removed it when i read several threads saying that the card could give me this error.  Removing it did not solve the problem.

The livecd works fine on my laptop, and the new desktop boots into a windows 7 install disk fine.

What else can I try to get ubuntu to install?

---

### Post by wilee-nilee on 2012-06-02
> **erith2000 said:**
> I just built a new computer and am attempting to install ubuntu 64 bit on it.  I am able to get to the purple try ubuntu/install ubuntu/check disc to defects/... screen, but nothing I have tried will get me past there.  It hangs on a black screen with a flashing cursor.

I had installed an nvidia 550 ti video card, but removed it when i read several threads saying that the card could give me this error.  Removing it did not solve the problem.

The livecd works fine on my laptop, and the new desktop boots into a windows 7 install disk fine.

What else can I try to get ubuntu to install?

At the screen you describe hit f6 and tick nomodeset, and boot in.

---

### Post by erith2000 on 2012-06-02
This gives me the same problem.

Is there any other information about the computer that would be useful?

---

### Post by erith2000 on 2012-06-03
I was able to get ubuntu to install by first installing windows 7 and using the windows installer.  Are there any steps i can take from here that would help with my booting problem?

---

### Post by btwThieves on 2012-06-03
This sounds like something I'm trying to deal with right now. The cause of my problem was a bad graphics driver that is making X crash. Passing "nomodeset" didn't make a difference for me, either. The workaround I found was to force the use of the VESA drivers for your card. To do that on a livecd, select "Try without installing", hit F6, turn on "nomodeset", hit escape to edit the boot line, and add (before the "--") the following:
```
vga=normal
```
This should disable the framebuffer and force the use of the VESA driver. If it doesn't, try looking around online for how to force VESA using different kernel options.

Forcing VESA will allow you to proceed with your install and troubleshoot the problem from there. The "magic" of Ubuntu is that a lot of the time, the problem will correct itself if you perform a full install.

---

### Post by btwThieves on 2012-06-03
> **erith2000 said:**
> I was able to get ubuntu to install by first installing windows 7 and using the windows installer.  Are there any steps i can take from here that would help with my booting problem?

Yes. Since this sounds like an X crash, it would be very helpful if we could get a look at your /var/log/Xorg.0.log file. Can you get to a terminal? Does switching VTs do anything (<CTRL>+<ALT>+<F1> or <F2>)? If the livecd were working, I'd say you could try booting from there, mounting your HD, and copying the log file over.

---

### Post by wilee-nilee on 2012-06-03
Have you tried the failsafe boot from the recovery in the wubi install?

Since you have a wubi install now you might ask the mods for a header change, by reporting yourself, or call this thread solved and start a new thread, focusing on a wubi with wubi in the header.

Wubi help is available, but rather sparse, a header mentioning it will likely get you the help faster. ;)

---

