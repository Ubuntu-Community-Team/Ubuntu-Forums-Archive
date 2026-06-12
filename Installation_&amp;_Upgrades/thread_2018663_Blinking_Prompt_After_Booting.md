---
title: "Blinking Prompt After Booting"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by groonrix on 2012-07-06
Hi all.
I'm failing to boot Ubuntu 12.04 (Live CD desktop amd64 edition)-

After choosing **Try Ubuntu** from the menu, I get stuck in a black screen with a **Flashing Prompt** for more than 15 minutes, that does not repsond to any keystroke. :(
I guess the problem has something to do with Graphics Drivers, but I can't really be sure.

I am using an nVidia GeForce GTX550Ti Graphics Card.

Any help?
Thanks in advance!

---

### Post by groonrix on 2012-07-07
Maybe using different drivers (rather than **Nouveau**) will mend the problem?
Is there any way to install ubuntu using **nVidia's properiatery drivers**?

---

### Post by efflandt on 2012-07-08
I am surprised you got that far.  My GTX 550 Ti would not even get to the "Try Ubuntu" gui for 12.04 install iso on USB, just a blinking cursor indefinitely.

While booting install CD, press a key on first purple screen with symbols at the bottom and enable **nomodeset** kernel boot parameter.  Then it should work.  The installed system should work without any boot parameters.

That is sort of opposite of 11.10 where I don't think I needed nomodeset for install, but needed it on the installed system.

---

