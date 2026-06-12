---
title: "firefox-3.1: artwork &amp; ugly fonts"
date: 2009-03-25
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Stetzen on 2009-03-25
I've installed firefox-3.1 and I've noticed a few strange things about it. First of all, it has extremely ugly fonts; it looks like subpixel smoothing is disabled (see the screenshot).
[http://lh5.ggpht.com/_ALTmOiA0mmE/ScqQdEsSwgI/AAAAAAAAEfA/Q0oktm2htMg/s1024/Screenshot-2.png]("http://lh5.ggpht.com/_ALTmOiA0mmE/ScqQdEsSwgI/AAAAAAAAEfA/Q0oktm2htMg/s1024/Screenshot-2.png")

And the second problem is that all firefox artwork is missing (yes, I like those red fox). Have anyone seen these problems?

---

### Post by JohnJackson on 2009-03-25
404 error with that link.

I have beta 3 installed and do not have any problems with font rendering. Also it is common in my experience for pre-releases of Firefox to have different artwork to final releases, for reasons I do not know. Perhaps to reiterate that it is not a stable version.

Edit: However I am unable to install add-ons directly through Firefox, not sure if this is because the add-ons website hasn't been updated to accommodate it yet.

---

### Post by Closed_Port on 2009-03-25
> **Stetzen said:**
> I've installed firefox-3.1 and I've noticed a few strange things about it. First of all, it has extremely ugly fonts; it looks like subpixel smoothing is disabled (see the screenshot).
[http://lh5.ggpht.com/_ALTmOiA0mmE/ScqQdEsSwgI/AAAAAAAAEfA/Q0oktm2htMg/s1024/Screenshot-2.png]("http://lh5.ggpht.com/_ALTmOiA0mmE/ScqQdEsSwgI/AAAAAAAAEfA/Q0oktm2htMg/s1024/Screenshot-2.png")

And the second problem is that all firefox artwork is missing (yes, I like those red fox). Have anyone seen these problems?

I'm seeing the same font problems.

---

### Post by Stetzen on 2009-03-25
[http://picasaweb.google.com/lh/photo/kkEQogRuiac2NKPp6dzBbQ?feat=directlink](http://picasaweb.google.com/lh/photo/kkEQogRuiac2NKPp6dzBbQ?feat=directlink)

About artwork: I've installed a windows version of ff3.1 on another PC, and artwork was there, so it seems to be a packaging problem

---

### Post by JohnJackson on 2009-03-25
Seems to be the font on that launchpad page. If you view the mozilla.org homepage in both they look exactly the same.

Edit: Looks like the artwork for the 3.1 alphas in Windows have the same artwork as in Ubuntu. I guess the artwork changed for the betas

---

### Post by simius on 2009-03-25
If I'm correct, the font problems are there because the beta builds are from Mozilla and use their own Cairo version that doesn't use GNOME's font settings. You can change the beta's font rendering by creating ~/.fonts.conf with your preferred settings. There are some example files on the Web.

---

