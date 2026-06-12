---
title: "LG L196WTQ Flatron LCD driver needed"
date: 2008-06-01
forum: Installation &amp; Upgrades
---

### Post by aqk on 2008-06-01
Hi - currently running an AMD duron with 396Meg with 8Meg SIS-630 onboard videocard.
 I attempted installing 8.04 with the above monitor and it just hung in a command screen during install.
 So I dragged out a dusty old HEAVY 15" VGA CRT monitor, and everything installed great.
  When I swapped back the LCD monitor, and re-booted, the Ubuntu 8.04 gave me the gray "unknown monitor" screen.
After messing around, I eventually got the graphics to work on the LCD, but only at 800x600 (or 640x480).

  Is there any way I can get a proper driver for the above screen to run it at 1440x900 or some similar resolution?

  PS-  it works quite well at this resolution (32m colors) when I boot it from my trusty old Win2000! W2K will LIVE FOREVER!

   Thanx.

---

### Post by cocopuffz on 2008-06-01
---------------
Just found a resolution to this problem! I was having this issue for weeks on end now...

"gksudo displayconfig-gtk" and then click on the "widescreen option, go detect display, scroll up to 1440x900... apply then log out. Log back in, and the res should now be an option available to you. It remains a "generic plug and play display" but it works.

---

### Post by spiepie on 2010-08-04
Hi did not understand that 
gksudo displayconfig-gtk no response when I ran the code

I have the same problem 

thanks

Si

---

### Post by aqk on 2011-01-11
Well, it's solved...  Upgraded to Win-7, and of course Ubuntu 10.10... 

Perhaps Win2000 will NOT live forever. (sigh)  
And who uses CRTs anymore, except to heat the room in these cold northern winters...

---

### Post by FunGuyDRW on 2011-06-21
I have the same problem as spiespie. Hooking a Flatron L222WT by LG Electronics to my 3-year-old laptop. Using Ubuntu 10.04. I'm googling for drivers, no success yet. Doing [COLOR="DimGray"]gksudo displayconfig-gtk[/COLOR] didn't bring up anything for me either.

---

