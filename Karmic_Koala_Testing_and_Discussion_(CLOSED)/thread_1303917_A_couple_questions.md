---
title: "A couple questions"
date: 2009-10-28
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Imoen on 2009-10-28
I have a nvidia 6200-LE on an Asus VW198 Monitor. When hooked up via DVI connector I get flashing pixels moving around where there's a light color next to a dark color. My xorg.conf file is totally empty. I uninstalled the nvidia 190 driver and did the sudo dpkg-reconfigure xserver-xorg in text mode as directed [here](http://ubuntuforums.org/showthread.php?t=83973).

My monitor book says these are the supported modes:
Res Freq-------H Freq----------V Freq-------Pixel
640x480--------31,469KHz-------60Hz---------25,175MHz
640x480--------37,861KHz-------72Hz---------31,50MHz
640x480--------37,50KHz--------75Hz---------31,50MHz
800x600--------35,156KHz-------56Hz---------36,00MHz
800x600--------37,879KHz-------60Hz---------40,00MHz
800x600--------48,077KHz-------72Hz---------50,00MHz
800x600--------46,875KHz-------75Hz---------49,50MHz
1024x768-------48,363KHz-------60Hz---------65,00MHz
1024x768-------56,476KHz-------70Hz---------75,00MHz
1024x768-------57,70KHz--------72Hz---------78,40MHz
1024x768-------60,023KHz-------75Hz---------78,75MHz
1152x864-------67,5KHz---------75Hz---------108,00MHz
1280x960-------60KHz-----------60Hz---------108,00MHz
1280x800-------49,702KHz-------60Hz---------83.5MHz
1280x800-------62,795KHz-------75Hz---------106.5MHz
1280x1024------63,981KHz-------60Hz---------108,00MHz
1280x1024------74,4KHz---------70Hz---------124,9MHz
1280x1024------77,9KHz---------72Hz---------134,6MHz
1280x1024------79,976KHz-------75Hz---------135,00MHz
1440x900-------55,935KHz-------60Hz---------106,5MHz
1440x900-------70,635KHz-------75Hz---------136,75MHz
1680x1050------65,29KHz--------60Hz---------146.25MHz

Ideally, I would prefer to use the nvidia driver, since it has 3d, but these flashing pixels are driving me mad. There's nothing wrong with my monitor, this issue only occurs on Ubuntu and only when using the DVI connctor. How do I fix this?

---

