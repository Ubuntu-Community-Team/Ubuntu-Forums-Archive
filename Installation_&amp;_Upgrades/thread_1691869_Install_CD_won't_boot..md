---
title: "Install CD won't boot."
date: 2011-02-20
forum: Installation &amp; Upgrades
---

### Post by Varik on 2011-02-20
I'm trying to breathe some life into a computer being ruined by Vista.  Here are the specs:

HP Pavilion Slimline s7700n PC 
AMD64 Athlon X2 2.0 GHz
1GB DDR2 
nVidia GeForce 6150 LE
HL-DT-ST DVDRRW GSA-H20 ATA Device

When trying to boot using the 10.10 64bit disk it starts to load, shows two icons at the bottom of a purple screen, then hangs with no monitor output.  The CD stops spinning.  No error output.

Also, I know the disk works as I've tried it on two other machines since.

Any ideas?  

Thanks!

---

### Post by Rocket2DMn on 2011-02-20
If you know that you are just going to install and don't need a live environment, check out the alternate installer.  It is a text based installer that works on more hardware - it is actually quite easy to use, so don't be scared away by the fact that it doesn't have the graphical environment with a mouse.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

### Post by sikander3786 on 2011-02-20
Welcome to the forums :-)

You need to put in the nomodeset boot parameter. See here and post back if you've any queries.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by Varik on 2011-02-20
I'll give it a shot, thanks.

---

### Post by Varik on 2011-02-20
Even with hitting keys, I can't reach the menu.

---

### Post by wojox on 2011-02-20
> **Varik said:**
> Even with hitting keys, I can't reach the menu.

It's the left shift key.

---

### Post by Varik on 2011-02-20
Ahah, that worked! The guide above didn't mention that!

---

### Post by sikander3786 on 2011-02-20
> **Varik said:**
> Ahah, that worked! The guide above didn't mention that!
Thats surprising. Apologies that guide has been written by me but I am pretty sure that pressing _any_ key works. I have tested it many many times on many systems. Don't know why it didn't work for you :-k

This page also mentions the same.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

Anyways, what is the progress after using nomodeset parameter?

---

