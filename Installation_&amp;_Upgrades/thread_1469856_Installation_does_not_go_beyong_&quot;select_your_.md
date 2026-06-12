---
title: "Installation does not go beyong &quot;select your keyboard&quot;"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2010-05-02
I am trying to install Ubuntu 10.4 on an AAO 160 GB but my installation process does not go further the keyboard selection (step 3 of 7) 
the mouse cursor shows the installation is on (round instead of arrow) but even if I wait 30 minutes it does not go further...
I can quit the installation though, but if I try again it will also stop at the same point

I have tried with two different USB pens and I have downloaded the ISO image twice (once from the site and once from torrent) and created a USB boot disk twice...

any idea of what is the cause?

---

### Post by utnubuuser on 2010-05-02
You could try switching ACPI off or maybe low-graphics mode by selecting those options with F4 at sartup.  I had the same issue with 9.10.

---

### Post by abelito8 on 2010-05-03
Thank you, I pressed F4 and then played with the F and at F6 I found that to disable ACPI ... acpi=off (does it mean in a terminal? If so...when?)

I had no idea so I waited until I arrived at step 1 of the installation and then called a terminal with ctrl+alt+F2 and then typed acpi=off

but when I tried to install ubuntu it did not work, I guess I did something wrong...

---

