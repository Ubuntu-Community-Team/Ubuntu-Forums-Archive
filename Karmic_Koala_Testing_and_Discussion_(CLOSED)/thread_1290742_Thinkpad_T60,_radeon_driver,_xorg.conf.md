---
title: "Thinkpad T60, radeon driver, xorg.conf"
date: 2009-10-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by mperry on 2009-10-13
I understand through a bunch of reading that the new xorg in karmic no longer needs a xorg.conf file and I duly am not using one. In Jaunty, I needed to set:

Option     "AccelMethod"        	"XAA"

To get rid of screen artifacts and flashing on the screen when I opened an application like firefox. On Karmic this setting appears to have no affect at all. To get rid of screen artifacts now I need to use the normal visual effect setting. If I set it to none, the ATI Technologies Inc M52 [Mobility Radeon X1300] seems to revert and show a lot of screen flashing. The settings above seem to have no effect at all. I also had no virtual terminals after X launched but read some bug reports and got that fixed. 

This also seems to have gotten more noticeable with the latest kernel upgrade I did yesterday or so. I'm running 2.6.31-13.45.

---

