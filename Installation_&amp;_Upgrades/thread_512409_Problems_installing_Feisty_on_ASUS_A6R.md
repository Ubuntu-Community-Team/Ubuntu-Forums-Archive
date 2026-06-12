---
title: "Problems installing Feisty on ASUS A6R"
date: 2007-07-29
forum: Installation &amp; Upgrades
---

### Post by miromurr on 2007-07-29
I am trying to install Ubuntu 7.04 on a ASUS A6R laptop with XP preinstalled. After booting with "live acpi=off" the live CD stops with the message "Kernel panic - not syncing:VFS: Unable to mount root fs on unknown block(104,1)".

Any suggestions?

I have tried Ubuntu 6.10 previosly, and here the live CD worked, but when I asked it to format the rescue partition (about 40 Gb out of 80 Gb harddisk) everything froze. I had no time back then, and hoped 7.04 would be better... Hmm!

Thanks in advance.

---

### Post by Pumalite on 2007-07-29
Memory?. Graphics?. Alternate CD ( text mode ) is always a good idea.

---

### Post by miromurr on 2007-07-30
Thanks for answering, Pumalite. My memory is 1024 Mb, and I dont know about graphics.

Before I tried your suggestion about the alternate CD, I tried to validate the CD, as it was a RW-CD. The Ubuntu menu tried to run Ubuntu instead, so I repeated the test on my stationary computer. No problem: fine CD. I tried the laptop again, but it would not validate the CD. Strange.

By acident I hit ESC and tried "live vga=771 acpi=off" at the boot-prompt, just for the hell of it. It worked!!??! A bug in the Ubuntu live-installer only affecting Asus laptops? Or stupid me first using the boot-promt I reached via F6...? Where does it say the boot-promt come after hitting ESC?

---

### Post by Pumalite on 2007-07-30
Glad it worked for you! Will file your experiences away, for future reference.

---

