---
title: "Unable to install programs (Opera)"
date: 2007-06-20
forum: Installation &amp; Upgrades
---

### Post by Geohevy on 2007-06-20
I finally took my chances and downloaded Ubuntu. I have spent less than two hours with the OS and already like it more than XP. In fact, I plan to get rid of XP altogether very soon. The way this OS flows together (and isn't full of holes and recycled icons from a decade ago) really give it an edge over XP.

 But I have a few problems; I downloaded Opera, and pressed the "Install Package" button, and everyhting went smoothly. But now I can't find it! Help me, please!

---

### Post by raja on 2007-06-20
Do Alt-F2 and type Opera in the box to confirm that Opera is installed and working. If it is not there in the menu, try ```
killall gnome-panel
``` After that check the menu again.

---

### Post by Geohevy on 2007-06-20
Okay, I have Opera running. But how do I set it as the default brwser, and put it on the topbar? And how do I install FlashPlayer?

---

### Post by swoll1980 on 2007-06-20
System>preferences> preferred applications

---

### Post by swoll1980 on 2007-06-20
[www.adobe.com](www.adobe.com) download linux .tar.gz version to desktop right click and extract the file navigate to file in terminal by using the command 

cd ~/Desktop/install_flash_player_9_linux                   make sure you use capital D then hit enter
Then follow these instructions

  
   
   4. type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by Colonel Kilkenny on 2007-06-21
> **swoll1980 said:**
> 
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

He/she probably wants it to work with Opera so I add couple things.
After installation go to Opera preferences -> Advanced -> Content and search the correct place where you'll find detected plugins and plugin options (I'm at WinXp-machine atm so I cannot remember the exact path to correct menu). Anyway you should click the "find new plugins"-button and hopefully Opera detects libflashplayer.so

---

