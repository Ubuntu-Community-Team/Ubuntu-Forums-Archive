---
title: "ThinkPad R51 Feisty video resolution problem"
date: 2007-05-07
forum: Installation &amp; Upgrades
---

### Post by openBA on 2007-05-07
After upgrade from Edgy to Feisty I have to notice major resolution problems on my IBM Thinkpad R51 with ATI R-9000 and external Samsung SM-244T.

Instead of used 1920*1200 resolution on Samsung external monitor, I can now see only in 1400x1050 resolution!

I browsed the forums, tested all Ubuntu advices, and found:

1) Fglrx driver is  not working on TP-R51 with ATI Radeon 9000 at all! Can't open the screen!
2) ATI driver is capable of maximum 1400x1050 
3) VESA driver is capable of 1600x1200 but only in KUbuntu! In Ubuntu it uses 1280x1024 resolution, but it display's  diagonaly which I obviosly do not like.:confused: 
4) ENVY  in automatic installation mode reports driver-HW-OS incompatibility in manual mode it install's MESA drivers, which have the same performace as ATI driver, barely 1400*1050

Is there any solution to that problem, which was not existent in Edgy?  
Should I return to Edgy, or will this issue be solved in the nearest future? * hope some people from Ubuntu read this *

---

### Post by openBA on 2007-05-10
This was quite promising, but no luck again. 

[http://ubuntuforums.org/showthread.php?t=432554&highlight=feisty+upgrade+ATI+xorg+7.1](http://ubuntuforums.org/showthread.php?t=432554&highlight=feisty+upgrade+ATI+xorg+7.1)

For now, the only working solution is back to very nice Edgy and use ENVY 0.9.1 to  install ATI's  driver ver. 8.28.8, the last one which is supporting MobileRadeon 9000.

I only hope that open driver authors won't let us down, as the ATI guy's did!

---

