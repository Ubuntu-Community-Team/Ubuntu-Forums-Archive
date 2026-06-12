---
title: "Installition error brings dots and white maze?!?"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by Muskito on 2011-04-25
Hello!!!
I'm  a really new user to ubuntu... I have never used or saw it on a Pc or Laptop and i wanted to try it out on my Tobi ( Toshiba Qosmio X550-Q890)...

I did everything right with the usb drive guide... and i get an image of space dots and blank white stripe going vertically and horizontally, Now the weird thing is i hear the ubuntu opening sound but nothing else... 

I have posted my system specs below, can anyone tell me what this means please?

Thank you!

* I am running windows on the ssd drive, the ubuntu was supposed to go on the sata drive.

--------------

Operating System
    MS Windows 7 Ultimate 64-bit SP1
CPU
    Intel Core i7 740QM  @ 1.73GHz
RAM
    6.0GB Dual-Channel DDR3 @ 528MHz (kinda lame but hoping to get this fixed :P)
Graphics
    NVIDIA GeForce GTS 360M 
Hard Drives
    63GB TOSHIBA TOSHIBA THNS064GG2BBAA (SSD)
    488GB Hitachi Hitachi HTS725050A9A360 (SATA)

---

### Post by Quackers on 2011-04-25
Welcome to UF.
Whilst booting hold down the shift key until the grub menu appears.
With your Ubuntu installation highlighted press the "e" key
On the new screen using the arrow keys, navigate to the end of the line which currently ends with "quiet splash" (but without quotes). Using the backspace key delete "quiet splash" then type in nomodeset then press ctrl + X
Does it now boot?

---

