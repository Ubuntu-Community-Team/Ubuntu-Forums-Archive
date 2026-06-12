---
title: "Boot disc: Splash screen. No video"
date: 2010-06-08
forum: Installation &amp; Upgrades
---

### Post by clobercow on 2010-06-08
Hello. I'm attempting an install of 10.04 on my pc

Specs:
Core i7
Gigabyte UD5 board
ATI 5870  (HDMI and DVI) tried both
Sharp screen. Supports many many resolutions including my bios resolution. 

Symptom: I boot the disc. I get through post. It starts to load the CD. I get a black screen, then I get a purple screen, and then I get a black screen and no response.

This happened on 9.04 also.

Linux Mint, latest version,  will boot with video, and install with video. 

Any help would be appreciated to get video on the boot CD. :???:

---

### Post by ronparent on 2010-06-08
The fact it boots with mint is encouraging. Mint is based on Ubuntu.

A boot parameter may be needed to correct. You should probably run the  'try with no changes' to debug the boots problems. When the boot menu posts, hit f6 to select boot parameters. You might try nomodeset 1st. Also delete **quiet splash** from the boot line - it appears on screen when you hit f6. Just hit <end> and backspace over quiet splash to erase. Although you often have to try one or more f6 options in diferent combinations, from what you describe it is more likely to be display related - either nomodeset or deleting the splash. I have ATI 5770 and only had a problem initially trying to install with two monitors plugged in. After installing the OS I installed the ATI drivers and everything works fine.

Post here if you need more help. Good luck.

---

### Post by clobercow on 2010-06-08
Thank you for the reply. I will check into that.

I do not see any options when the CD starts to load. Only a purple screen for a shot time and then blackness. I'm not sure how I could get to "try with no changes". I do not see the boot menu.

---

### Post by CyClyst on 2010-06-30
press esc during first purple screen or one of the F keys (F1-F6) that should bring up the menu. I am having the same problem and I am going to go home in 30 min to try and install ubuntu again =D GOOD LUCK

---

### Post by clobercow on 2010-08-08
Does anyone know if there has been a fix for this? I've been searching around. I haven't seen much.

I've been able to get into safe video mode and install drivers, but its really not working.

---

