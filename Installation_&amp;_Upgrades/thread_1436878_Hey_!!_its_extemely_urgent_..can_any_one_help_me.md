---
title: "Hey !! its extemely urgent ..can any one help me??"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by pandeylavakesh on 2010-03-23
Actually, i upgraded to ubuntu 9.10 from 9.04 today .but after upgrading so many errors crept in .
and these are following ..
1. Original login screen of ubuntu 9.10 is not being displayed.
2.By mistake i removed volume control and network connection applet from upper pannel.
so can any one tell me how to re organise the pannel...and get back those two applets or can any one tell me how to completely recover the upper pannel....
please reply me fast ..i am in great trouble.

---

### Post by iponeverything on 2010-03-23
> 1. Original login screen of ubuntu 9.10 is not being displayed.

don't know what you mean.

> 2.By mistake i removed volume control and network connection applet from upper pannel.
so can any one tell me how to re organise the pannel...and get back those two applets or can any one tell me how to completely recover the upper pannel....


On the upper panel on the right hand side you should see three small horizontal lines. The is the notification area. Right click on the small horizontal lines  and choose "- Remove from panel". Then right click in the same area and choose "+ Add to Panel" go though the list and find "notification area" then click on "Add"

---

### Post by pandeylavakesh on 2010-03-24
Thaks a tonn for giving me back my notification area . :)
Okk....am sorry for not clarifying my 1st problem. Actually I meant to say that My original boot screen that comes in Ubuntu 9.10 is not coming . That  light grey boot screen with UBUNTU written  there , having progress bar below UBUNTU ...and light falling from back to UBUNTU ...n all that .
Since this screen is very cool so I want that back .
Please help me ...!!!

---

### Post by uRock on 2010-03-24
So, you mean the boot splash isn't coming up. Are you getting just the text output while it is booting?

---

### Post by michaelzap on 2010-03-24
> **pandeylavakesh said:**
> Thaks a tonn for giving me back my notification area . :)
Okk....am sorry for not clarifying my 1st problem. Actually I meant to say that My original boot screen that comes in Ubuntu 9.10 is not coming . That  light grey boot screen with UBUNTU written  there , having progress bar below UBUNTU ...and light falling from back to UBUNTU ...n all that .
Since this screen is very cool so I want that back .
Please help me ...!!!
Karmic uses Grub2 and GDM2, which is different from Jaunty and previous versions. Your previous GDM themes will no longer work with Karmic, and it's not easy to customize GDM2. There are some scripts and tools available to change it somewhat (e.g., [http://ubuntuforums.org/showthread.php?t=1358026](http://ubuntuforums.org/showthread.php?t=1358026) ), but it's not nearly as malleable as the old GDM.

---

