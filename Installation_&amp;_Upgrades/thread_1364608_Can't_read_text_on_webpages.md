---
title: "Can't read text on webpages"
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by nerdtron on 2009-12-26
I'm not quite sure if this is the right forum to post but I have this problem and really bugs me.
 I recently installed karmic on my PC and it runs great. The screen resolution was a good 1024x768 for my small monitor. The texts are nice and sharp. After playing with it for a few days  and installing updates too, I found an option to enable desktop effects and Karmic ask me download and install video card driver for my Nvidia 8100. I click Yes and the installation was automatic. 
But now, everytime  I reboot the resolution was reduced to 800x600 (I need to change it back manually to 1024x768 ) and every time i scroll a webpage, the text become clipped or distorted (I need to press Ctrl+A, or highlight all text to read it properly) . What could have caused this? I don't want do disable the eye candy special effects thingy....
Any suggestions please?..

---

### Post by gsmanners on 2009-12-26
With the nVidia driver going, you can change the display by typing the following in a terminal:

gksudo nvidia-settings

That will let you change how the display is set up and you can save those changes to the "X Configuration File" when you're done.

---

