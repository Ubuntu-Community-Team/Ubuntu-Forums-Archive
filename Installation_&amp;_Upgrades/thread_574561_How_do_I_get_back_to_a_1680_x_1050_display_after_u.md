---
title: "How do I get back to a 1680 x 1050 display after upgrading to Gutsy?"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by cayhorstmann on 2007-10-13
I have a Thinkpad X60 with Intel Graphics. Laptop resolution is 1400x1050. My monitor is a Dell with 1680x1050. It worked in Feisty, and now I upgraded to Gutsy, and everything broke. My display is now a shitty 800x600. I tried restoring the old xorg.conf, but it made no difference. 

I tried that System -> Administration -> Screens and Graphics configuration tool, but it is dumb, dumb, dumb. It lists "greyed out Screen1", "Screen 1", and "greyed out Screen 2" (huh?) It correctly recognizes "Screen 1" as Dell 2005 FPW (Analog). It only offers two resolutions: 800x600 and 640x480, at 73hz. Hello, Ubuntu, these monitors have been the cause of hundreds of complaints in Feisty. 

I tried both the i810 driver and the "experimental mode setting driver". Neither seemed to work.

Help! I don't want to boot back into Vista.

Cay

---

### Post by cayhorstmann on 2007-10-13
I'll answer my own question. The key is to use the "experimental mode setting driver". I had to try several times to select that--the setting kept reverting to the i810 driver. Eventually, it stuck, and now I can select the 1680x1050 resolution.

---

