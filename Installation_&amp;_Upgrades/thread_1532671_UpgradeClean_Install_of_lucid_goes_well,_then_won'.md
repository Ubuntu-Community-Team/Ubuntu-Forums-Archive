---
title: "Upgrade/Clean Install of lucid goes well, then won't boot on restart"
date: 2010-07-16
forum: Installation &amp; Upgrades
---

### Post by Toriam on 2010-07-16
I have been trying to install/upgrade xubuntu from 9.10 to 10.04 on two laptops, an Acer aspire one (installed sucessfully) and an older Gateway M210. I have tried both metholds with xubuntu and ubuntu. It goes just fine, untill I reboot. It starts to boot, with the new black and white logo looking a little pixelated. Then goes to a black screen and hangs. Right after the logo comes on it has a line right under the logo talking about pressing S or M to continue. Both actions make no difference. Another post talks about changing the resolution of the monitor, but its different than my situation and about another graphics card. And suggestions?

---

### Post by oldfred on 2010-07-16
Do you get a grub menu, or by holding down the shift key until the menu appears do you get a menu?

Try recovery mode.

Try editing the boot line and replace quiet splash with nomodeset.

---

### Post by Toriam on 2010-07-16
I saw no menu. Next time I try and install I'll give these things a try. Thanks! I'l let you know what happens. I'll probably get on installing tonight.

---

### Post by Toriam on 2010-07-19
I've tried all you suggested, oldfred. Nothing was any different. I tried the other f6 options at the menu area of the install cd. BTW, I always use the alt install CD on my machines.I guess this laptop just really likes 9.10? I'm wanting the new 10.04 features though :(  .

---

### Post by oldfred on 2010-07-19
The alt install CD is not a liveCD so I am not sure of how you get to modify to boot parameters. It used to be a choice or maybe still an Fx key to select boot settings.

---

### Post by colinpat on 2010-07-20
Same probblem after an upgrade from 9.10 to 10.04 on an Acer TravelMate 660
Boots up to a black screen - no grub menu just a big black screen.
Anyone have any ideas on what the problems are or how to fix them??

---

