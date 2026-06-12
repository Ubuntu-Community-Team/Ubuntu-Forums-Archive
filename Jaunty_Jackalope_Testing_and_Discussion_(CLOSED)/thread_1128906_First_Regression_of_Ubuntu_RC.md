---
title: "First Regression of Ubuntu RC"
date: 2009-04-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bigbrovar on 2009-04-18
One of the feature i was praying would be implemented in ubuntu is the ability of Intel GMA965 cards to support dual monitor and compiz at the same time. my pray was answered then the mesa package with the fix was release as update during the the beta, however to my dismay upon installing the ubuntu rc (clean install) its back to the bad old days :(, am unable to have compiz and dual monitor again.. everytime i try to setup dual monitor, compiz get disabled .. can any one confirm this

---

### Post by zoldiel on 2009-04-18
The issue with the card is that the maximum texture size of the card is 2048x2048, if you are using two monitors side by side at 1280x800 or 1280x1024 your display width is 2560. 

You can still run compiz by adding SKIP_CHECKS=yes to ~/.config/compiz/compiz-manager, logging out and logging back in. 

Compiz will draw the desktop up to a width of 2048, after that there will just be a black area or a whole in the desktop cube. If you disable the nautilus desktop and use the wallpapers plugin for compiz this will alleviate the issue, as compiz will treat each screen as a seperate texture. 

Also, you could set your displays so that one is above or below the other, rather than side by side, this should keep you under the 2048x2048 limit.

---

