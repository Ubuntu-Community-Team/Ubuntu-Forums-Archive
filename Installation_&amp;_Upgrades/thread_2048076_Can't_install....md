---
title: "Can't install..."
date: 2012-08-26
forum: Installation &amp; Upgrades
---

### Post by obithius on 2012-08-26
Hi, I have a bit of a problem I hope someone can help me with.
I have attempted a fresh install of ubuntu. The live disc runs fine, and it seems to install fine. When it restarts to complete the installation I get a black screen with a few wiggly orange lines at the top, and nothing more. I can even hear the login prompt sound asking for my password.
I've tried ubuntu 32 bit, 64 bit and mint, but all have exactly the same outcome.
My system:
AMD Phenom II X6
ASUS M4A79XTD EVO
AMD Radeon HD6950

Many thanks in advance!
Chris

---

### Post by mick463 on 2012-08-26
Have you tried running ubuntu on another graphics card or the inbult vga adapter (if you have one). If that works you can then look for a driver for your other graphics card.

Regards Mick463.

---

### Post by obithius on 2012-08-26
I don't have another graphics card, and the only output is on the card...so kinda stuck there. 
It won't install proprietary drivers during installation will it?

---

### Post by mick463 on 2012-08-26
Not that i know of but you can buy a cheap $30 to $50 card if that is not an option you could borrow a working card of a mate. I will do a bit of research on that for ya though.

Regards Mick463.

---

### Post by mick463 on 2012-08-26
I am not sure this will work but you can try download them through the live cd but install them on your ubuntu partition.

Try this it might work fingers crossed.

[http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/](http://thedaneshproject.com/posts/ubuntu-11-04-blank-screen-on-boot-solved/)

---

### Post by obithius on 2012-08-26
Thanks for the ideas, I'll keep trying!

---

### Post by mick463 on 2012-08-28
[http://ubuntuforums.org/showthread.php?t=2046591](http://ubuntuforums.org/showthread.php?t=2046591)

Go to that thread sounds like your problem.

---

### Post by mick463 on 2012-08-28
Strewth pressed the wrong key.

---

### Post by mastablasta on 2012-08-28
> **obithius said:**
> I don't have another graphics card, and the only output is on the card...so kinda stuck there. 
 
Just after BIOS loads press Esc repeatedly (or left shift) to enter GRUB boot loader
 
then first try to boot with nomodeset parameter: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
-- 
if nomodeset doesn't work, boot again and select recovery mode. Then go to CLI.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)
 
here you can install the proprietary drivers. maybe you can even access low graphics mode.
 
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
 
> 
It won't install proprietary drivers during installation will it?
 
No.
 
BTW can you boot into liveCD (liveUSB)?

---

### Post by obithius on 2012-08-28
Thanks for all your advice. I managed to get into recovery mode by holding shift, and from there it let me get to the desktop. The aspect ratio was well off and I couldn't alter it, (which is odd because it was fine on the live cd)  but I could see enough to install the right drivers. Restart and it booted fine.

---

