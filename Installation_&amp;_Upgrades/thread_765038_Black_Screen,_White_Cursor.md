---
title: "Black Screen, White Cursor"
date: 2008-04-24
forum: Installation &amp; Upgrades
---

### Post by quietas on 2008-04-24
Hey folks, I've got a new Dell Optiplex 320 here at work. Decent specs, great for Ubuntu actually. Anyway I'm trying to install Hardy desktop on it, but both the RC and release version hang at a blank screen with a white cursor in the upper left.

Any ideas?

---

### Post by Peter09 on 2008-04-24
Try booting into safe mode and typing startx at the terminal prompt.

What graphics card have you got?

PC

---

### Post by thethimble on 2008-04-26
I believe I'm having a similar problem [here]("http://ubuntuforums.org/showthread.php?t=769268").

---

### Post by Ilan on 2008-04-26
I join the club... tried all the menu options, managed to do an installation in safe mode but it is unusable (messy screen, blurred text). Tried new installation under detailed mode it freezes after
(hd0,0)
filesystem type is ft, partition type 0xdc
[Linux-bzImage, setup=0x2a00, size=0x1ce278]
[Linux-initrd @ 0x17863000, 0x77c500 bytes]

at this point the machine goes into deep freeze

---

### Post by Elycian on 2008-04-26
I'm having the exact same problem, in fact I had the exact same problem with 7.10 back in October.. If you can find a solution or if anyone can post a solution I'd be pretttyyy happy :] lol

---

### Post by zgoda on 2008-04-28
I'll try with LILO as boot loader, this might help (in fact, this helped me to boot Debian Etch on this crap). Anyway, I'm gonna definitely replace my old 7.04 with something bit newer, be it Ubuntu 8.04 or Fedora 9. I know OpenSuSE 10.3 installs and boots on Optiplex 320, but it's crap.

---

### Post by Peter09 on 2008-04-28
might be worth a try with the alternate CD, thats a non-graphical installer.

PC

---

### Post by zgoda on 2008-04-28
Alternate install runs bit faster, but to be able to replace bootloader you'd have to use livecd anyway.

---

### Post by quietas on 2008-04-30
From what I can tell this is a limitation of the Optiplex 320. If you do a search, you'll come up with lots dealing with v6, 7 and now 8 of Ubuntu. It's a poor design from Dell. Great for Windows, bad for Linux. Lilo and Grub2 work, but not Grub 1.

---

### Post by Rocky37 on 2008-05-01
> **quietas said:**
> From what I can tell this is a limitation of the Optiplex 320. If you do a search, you'll come up with lots dealing with v6, 7 and now 8 of Ubuntu. It's a poor design from Dell. Great for Windows, bad for Linux. Lilo and Grub2 work, but not Grub 1.

Strange.  I have the same problem on my desktop - and it's not even a Dell.  :lolflag:

---

