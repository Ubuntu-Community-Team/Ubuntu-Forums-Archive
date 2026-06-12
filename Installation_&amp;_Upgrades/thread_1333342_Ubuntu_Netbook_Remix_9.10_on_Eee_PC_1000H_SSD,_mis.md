---
title: "Ubuntu Netbook Remix 9.10 on Eee PC 1000H SSD, missing clock"
date: 2009-11-21
forum: Installation &amp; Upgrades
---

### Post by T1Oracle on 2009-11-21
So I have an EeePC 1000h with the 40GB of SSD, 8GB is fast SSD, 32GB is slow SSD.

When I bought my Eee I wiped the Xandros off and installed Easy Peasy 8.10.  Then I upgraded to 9.04.  Then yesterday I decided to dump Easy Peasy for UNR 9.10.

When I had Easy Peasy I removed the swap partition so that I would not burn up the SSD with excess writes.  I also hacked Firefox to eliminate it's disk cache.

When I installed UNR 9.10 I remembered that the swap is needed for hibernate but I could not remember how I fixed that.  Regardless, I tried to install it without modifying the partitioning.  This was a mistake because while UNR worked perfectly it did not mount my 32GB SSD as the /home folder so I did not have my files or my disk space (8GB is tiny).

So I redid my install and manually set up the partitioning to not have a swap partition, and to use my 32GB mounted as my /home folder.

Now I notice that the bar at the top of the screen is no longer black, it is light gray.  It is also missing the clock, the battery indicator, the wireless, and just about all of the features UNR had the first time I tried it.  The only thing that shows up there is the light gray bar with the letter icon for Empathy and Evolution.

How do I get the standard UNR panel back?

Also, I did a "ps aux" and gnome-panel is running so I figure it must be broken somehow.

Any help is greatly appreciated.

---

### Post by T1Oracle on 2009-11-22
I figured it out.  Apparently if you right click the panel at the top, unlock it, and drag the bar next to the Ubuntu icon over, you expose enough of the panel to get to the panel menu.  If you right click on the panel between the Ubuntu icon and the vertical bar (the thing with the dots) you get a menu that shows Add To Panel, Properties, New Panel, etc.

I added the Notifications Area and the Clock and all was back to normal.  The colors were a matter of the installed theme.

That menu should be made more intuitive.  At the least there should be an icon in the preferences area that would let you do the same thing.  Sometimes a little duplication is a good thing when it makes things easier to find.

---

