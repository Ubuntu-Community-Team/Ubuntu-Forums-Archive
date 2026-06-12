---
title: "noob- Need Larger Icons Menus etc. Changing Screen Resolution Doesn't Help"
date: 2005-09-30
forum: Installation &amp; Upgrades
---

### Post by prs444 on 2005-09-30
Hello all! I have been fooling around with the live cd and most everything seems to work fine. I have a Dell Inspiron 8200 PC with a very high resolution screen.  This makes all the menus and icons very tiny. In Windows XP I changed the screen resolution down to 1024 x 768 and that made the icons bigger and the screen much more readable.
I tried to change the screen res in ubuntu and what happened was the screen shrank down in size, leaving a large black frame around the window.
Is there any way to make the lower resolution setting display in the full screen?:confused:
This is the only real issue I need to resolve for me to make the jump to Linux.
Any help would be great!
Thanks!

---

### Post by Alexander Kirillov on 2005-09-30
[QUOTE=prs444]Hello all! I have been fooling around with the live cd and most everything seems to work fine. I have a Dell Inspiron 8200 PC with a very high resolution screen.  This makes all the menus and icons very tiny. In Windows XP I changed the screen resolution down to 1024 x 768 and that made the icons bigger and the screen much more readable.
I tried to change the screen res in ubuntu and what happened was the screen shrank down in size, leaving a large black frame around the window.
Is there any way to make the lower resolution setting display in the full screen?:confused:
This is the only real issue I need to resolve for me to make the jump to Linux.
Any help would be great!
Thanks![/QUOTE]
Much better way would be to keep high resolution and choose "Large Print" theme in System-Preferences-Theme. Or you can keep the current theme, but manually increase font size (using System-Preferences-Fonts) and the size of icons used by file manager (System-Preferences-File Management-Default Zoom level).

---

### Post by eheintz on 2005-10-01
It appears your Windows driver is doing "screen stretching" to fill the screen when you are running at a lower than the LCDs native resolution. Your X driver is NOT, so when you set your resolution to 1024x768 it actually only users 1024x768 pixels of your screen, hence the black space surrounding the window.

Check your BIOS settings. Many laptops have an option to "fill screen" or "stretch screen". It may be a non-obvious setting and varies wildly from laptop to laptop. If you have such an option the hardware will automatically scale low resolution output to fill the entire LCD.

---

### Post by prs444 on 2005-10-01
Thank you both for your help!
I looked for the large print theme but it doesn't seem to be on the Live CD version. I did play around with making the fonts and icons larger and things look pretty good now.
I think this weekend I'm going to make the jump to Linux!
I'm in the process of moving all my vital files to a back up drive so I can access them from my other computer while I work out Linux!
Thanks again!

---

