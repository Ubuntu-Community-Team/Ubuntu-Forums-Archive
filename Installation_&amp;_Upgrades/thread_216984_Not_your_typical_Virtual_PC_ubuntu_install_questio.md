---
title: "Not your typical Virtual PC ubuntu install question"
date: 2006-07-16
forum: Installation &amp; Upgrades
---

### Post by eternal85 on 2006-07-16
Ok, I have been trying for well over a few hours now to get ubuntu to install in Virtual PC 2004. Here's my issue. IT WON'T INSTALL!!! When I choose to "Start or install ubuntu", it loads the kernel, then I get 2 error messages. "Checksum is invalid in Device 1" and "Checksum is invalid in Device 2", then it procedes to load up the live portion and finally give me that dreaded garbled screen problem everyone talks about. Now, unless I am completely missing something, but everyone's post's I am reading seems to have no problems installing. A thought I have is maybe that it HAS to load up the live portion before I can install it? Any help would be greatly appreciated. I have allocated 256MB to the virtual system.

---

### Post by mk83 on 2006-07-16
Have a look at [http://harry.sufehmi.com/archives/2006-06-28-1193/](http://harry.sufehmi.com/archives/2006-06-28-1193/)

> 1. When booting up from the CD, you’ll see a menu. Press ESC there, where it’ll tell you that you’re about to switch to text-mode. Choose OK

2. You’ll see a prompt like this : boot:

3. To continue, just type this: install debian-installer/framebuffer=false

4. Press Enter, and the screen should show up OK on VirtualPC 2004.


Cheers,
Martin

---

### Post by Commander South on 2006-07-17
I am having the same problem, however when I go into text mode and type the command listed I get the error: Could not find kernel image: install

Any ideas?  Thanks!

---

### Post by Commander South on 2006-08-02
anyone?

---

### Post by rhenriksen on 2006-10-26
I'm having the same problem installing Ubuntu 6.10 into a VirtualPC 2007 on Windows Vista RC2 (bld 5744).

---

### Post by tylau on 2007-02-23
JUST when you see the boot menu of ubuntu, press F4 and change the display mode to some 16bit color depth, before prooceeding to boot from ubuntu CD; then once you are booted, choose install to harddrive option from the top right side menu. :) :guitar:

---

### Post by dannyboy79 on 2007-02-23
what about trying to install the alternate install cd. this is a text based install.

---

