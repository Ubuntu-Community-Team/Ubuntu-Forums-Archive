---
title: "Sony Vaio VPCCW21FX Live USB black screen issue."
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by jaythedogg on 2011-01-01
Hi guys, first of all, specs:

Sony Vaio VPCCW21FX Laptop
Intel Core i3 CPU M 330 @ 2.13GHz 2.13GHz
4.00 GB DDR3
64 Bit 
Nvidia 310M with CUDA 256MB Dedicated Graphics Memory

Okay, basically I downloaded the 64 bit version of 10.10 Ubuntu from the official site, used pendrive linux to install it to my SanDisk 4 GB USB stick & put it in the laptop after setting the BIOS to boot from USB.

I started it, got the Ubuntu selection screen for liveCD, chose "Run Ubuntu from USB", I get all the scrolling text, then it goes blank screen, USB is still live (flashing from data read occasionally) & I get the Ubuntu spash sounds (Like at the splash screen).

Any help? I can't figure it out with searches either. I am reading about people who have graphics issues & freeze, but I get the sound each & every time & it appears to try to load, but no screen. Any help guys?

---

### Post by jaythedogg on 2011-01-01
In order to edit my grub.cfg file in /boot/grub.cfg on my USB, where do I put nomodeset?

Nevermind this question... Any idea on the main issue?

---

### Post by jaythedogg on 2011-01-03
See original question

---

### Post by jaythedogg on 2011-01-10
Been nearly a week, has anyone a clue about how to address this issue?

---

### Post by jaythedogg on 2011-01-13
Been three days since the last post, bump & any ideas?

---

### Post by Quackers on 2011-01-13
Can you use the live session from the cd by choosing the nomodeset option?
Press Esc key during booting from cd, choose language, press F6, choose nomodeset option.

---

### Post by Phis on 2011-01-14
The live session doesn't seem to work, you have to install using the alternative install. Here is the link to a related post for vpccw21fx

[http://ubuntuforums.org/showthread.php?t=1481842](http://ubuntuforums.org/showthread.php?t=1481842)

the video card install was also troublesome but now seems to have been fixed in the new nvidia driver. I suggest you read through the forum.

---

