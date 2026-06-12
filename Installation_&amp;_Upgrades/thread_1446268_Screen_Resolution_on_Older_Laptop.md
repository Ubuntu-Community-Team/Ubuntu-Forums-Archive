---
title: "Screen Resolution on Older Laptop"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by rixx72 on 2010-04-03
I just installed the latest version of Ubuntu on my Toshiba Sattelite A25-207 laptop.  I totally erased my previous Windows XP OS and everything else.  Everything is great, execept the screen resolution.  The resolution is set at 800 x 600 and I know that my screen can handle bigger.  How do I change this?

I am totally new to Ubuntu and I have no idea how to play with code.  Can someone please walk me through the fix step by step? 

Thanks!

---

### Post by mikewhatever on 2010-04-03
Try System->Preferences->Display.

---

### Post by rixx72 on 2010-04-03
Thank you for the reply.  However, I have tried that and the highest resolution is 800x600 and I cannot select anything higher.

Any ideas?

Thanks.

---

### Post by efflandt on 2010-04-03
Judging from [http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A25-S207.pdf](http://cdgenp01.csd.toshiba.com/content/product/pdf_files/detailed_specs/satellite_A25-S207.pdf) it has Trident CyberBlade XP2 graphics processor; 32 MB shared RAM that with external display can do up to 2048x1536 @ 60 Hz.  The native resolution of your laptop display is 1024x768, and system memory is 512 MB upgradeable to 1 GB PC2100 DDR SDRAM.

Post the output of **sudo lspci -v** related to your video and also look through /var/log/Xorg.0.log to see what X recognizes about it and your display.  Also post the output of **xrandr** command.  Use the **#** at the top of the message window to put code tags around formatted or any large amount of pasted text.

Normally Ubuntu would automatically use the native resolution of a laptop display, but I am not familiar with Trident and whether the trident X modules support your chip or if it is using vesafb (framebuffer).

See **man xrandr**.  **cvt 1024 768** or **gtf 1024 768 60** could find a modeline to use for xrandr which can be used to temporarily set and switch modes.  But I cannot tell you how to make modes permanent because I just use xrandr commands in a script when I connect my laptop to an external display.

---

