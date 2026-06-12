---
title: "Clean Installation Fail"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by firatagdas on 2010-05-13
Sorry for my english.

I tried a couple times installation ubuntu 10.04 64 bit. After the CD boot, Ubuntu logo show up. Then my monitor goes sleep. 

My configuration is:

AMD Phenom II X6 1090t 3.2
8 GB DDR3 RAM
Gigabyte Mainboard
Monitor: LG E2350V-PN 23 LED 5ms DVI

My purpuse is install Ubuntu to use first boot. But I cant install.

---

### Post by Grenage on 2010-05-13
If you press Ctrl-Alt-F6, does it display any text?  If F6 doesn't work, try F5 or F4 etc (my understanding of the differences is weak).

---

### Post by howefield on 2010-05-13
Do you get as far as the Desktop ?

If you get to the options menu (Try Ubuntu without installing, Install Ubuntu, Check disc for defects ect, ect) press the F6 key and select the nomodeset option. Then try to load.

If that doesn't work, as above but press the Esc key after pressing F6 (to clear the options dialogue) and remove --quiet splash from the end of the boot line. And try loading.

If that doesn't work, hopefully you will have a clue on screen as to why it is failing.

---

