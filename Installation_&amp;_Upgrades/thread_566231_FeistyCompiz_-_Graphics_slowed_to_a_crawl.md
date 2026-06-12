---
title: "Feisty/Compiz - Graphics slowed to a crawl"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by koytetsu on 2007-10-03
Well I finally got my HP nx9420 Laptop running Feisty and got Compiz installed without a hitch running XGL and the latest ATI drivers.

Everything seemed fine, I enabled some effects such as cube, all good.  But after a few minutes suddenly everything was running terribly slow.  Any graphical effects were slowed to a crawl and the system was totally unusable.  This problem was recurring after any number of reboots and trying different ATI drivers.  I also noticed my laptop video card fan was constantly running.

Now I had this same laptop running Beryl on 6.10 for months with no problem whatsoever.  Anyone seeing the same issues?  

Note:  I used the guide to install the latest Compiz Fusion from gutsy back onto Feisty, but no one in that thread seemed to have an issue with it.  Not sure if its an ATI, Feisty or Compiz issue.  Also I am running single monitor, 1680x1050.  Thanks

---

### Post by Soybean on 2007-10-03
Well... Compiz and Beryl *are* different, and I've heard of several cases where one or the other works better for someone. So you could consider switching back to Beryl, at least for the time being.

Alternately, you could try disabling as many parts of Compiz as possible, and see if that fixes it. If it does, then you can try them one at a time to see exactly which one is causing the problem.

Oh, how much RAM do you have? Could be you were close to your limit with Edgy/Beryl, and Feisty/Compiz is taking enough more memory that you're getting swapping problems. Looking at "top" sometime when you're having this problem could help you determine if this is the case.

---

### Post by koytetsu on 2007-10-03
1.5Gb of RAM, X1600 ATI Mobility 256 video card and 1.8ghz Cure 2 Duo CPU

Something to try would be Beryl of course, though there were some particular compiz fusion features I wanted.  I had to reinstall Vista last night so I could use my laptop at work today unfortunately.  Don't know if i want to cook this install again just to try Beryl.

---

### Post by Soybean on 2007-10-03
That ought to be sufficient memory. I seem to recall hearing about problems with Compiz and the mobility X1600, though... I don't know the details, but there may be a specific conflict there. 

Even if not, it kind of sounds like something that would take a fair bit of fiddling to fix. If you're not into fiddling, it might be worth waiting for a newer version to see if your troubles get sorted out on their own. :)

---

