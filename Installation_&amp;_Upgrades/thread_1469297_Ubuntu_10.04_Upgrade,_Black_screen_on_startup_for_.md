---
title: "Ubuntu 10.04 Upgrade, Black screen on startup for 10 seconds"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by GilbertEvanG on 2010-05-02
Hello,
Today I upgraded to Ubuntu 10.04 (from 9.10), and during boot I get a long black screen (for roughly 10 seconds) with a blinking cursor. After that, the purple Ubuntu splash screen shows up for about a half second before the login prompt appears and then everything functions normally.

Does anyone know how to make this black screen go away and have the splash screen show up for the whole time? I assume that is the intended behavior.

I've read several threads about a black screen after upgrade, but those sounded like the screen was permanent and never let them log in, which isn't the case for me. I can log in fine, it's just more of an annoyance to have a black screen during the boot up.

Thanks.

---

### Post by sunk8 on 2010-05-02
I had a similar issue. Installed a plymouth theme to get rid of it.

Search for plymouth in Synaptic. You'll find lots of themes in the repos.
I've got the ubuntustudio one installed, its really neat...

---

### Post by GilbertEvanG on 2010-05-02
I just tried that, and I get the same behavior unfortunately. My screen is black for several seconds and then I see the (new) splash screen for about a second before the login prompt appears.

---

### Post by GilbertEvanG on 2010-05-02
I stumbled across this: 
[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)
and it made a significant difference. Now I can actually see the loading screen for most of the boot up time!

---

### Post by drivindisco on 2010-05-03
Having identical issue on a Dell Inpiron e1505. Every fix for this seems to involve nVidia drivers... I have intel graphics. Anyone find a fix?

---

### Post by GilbertEvanG on 2010-05-03
I used the link posted above and have an ATI graphics card.

---

