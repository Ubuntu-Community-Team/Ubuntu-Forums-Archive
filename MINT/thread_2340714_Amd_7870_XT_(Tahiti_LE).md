---
title: "Amd 7870 XT (Tahiti LE)"
date: 2016-10-21
forum: MINT
---

### Post by General_Faliure on 2016-10-21
Hello.
This card doesn't seem to be supported in Linux Mint with the opensource driver.
I have installed Linux Mint 18 with a AMD 5850 and it worked fine.
I  have since upgraded the graphics card to an Amd 7870 XT, and now it  boots to a black screen with some garbled letters, then it reboots using  the software renderer, which is slow.
The card works fine in windows 10 (dual boot).
I  think Linux gets confused with the gpu chipset which is a Tahiti LE.  The normal 7870 is a Pitcairn, which is probably what Linux is  expecting.
I have installed the 4.8 kernel and the Padoka PPA, after i found out the card wouldn't work, but still no luck.
This is a known problem , which is persisting for over three years now.
See this bug report: [https://bugs.freedesktop.org/show_bug.cgi?id=60879](https://bugs.freedesktop.org/show_bug.cgi?id=60879)
Anybody some thoughts on this, or better yet a solution?

---

### Post by howefield on 2016-10-21
Thread moved to the "*MINT*" forum.

---

### Post by Bashing-om on 2016-10-21
General_Faliure; Hello;

A thought .. how old is this machine ?  Are you sure your Bios supports the newer hardware ?
That support for newer hardware is what I am presently experiencing on my machine.
If you boot your system with boot messages enabled ( remove 'quiet splash ' from the kernel boot line in grub )  do you see something like " unknown chipset"  ?

[INDENT][INDENT]it all starts in Bios
[/INDENT][/INDENT]

---

### Post by General_Faliure on 2016-10-22
Hello.
This pc is fairly new; socket 1150, Pentium 3258 (@4.2), 4 gig of ram.
The videocard works fine in windows, on the same system.
One time i got this message during boot: 
[0.746100] radeon 000:01.0: invalid pci rom header signature: expecting 0xaa55, got 0xffff.
So it looks like linux is expecting a different card.
I will try this card in a different machine later and do a fresh install, see if that works.
Linux does start after a few seconds, but in software rendering.

---

