---
title: "Firefox menu-fonts are too small?"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by handy on 2007-10-21
I did a fresh install of Gutsy's Kubuntu, which is impressive.

A problem I can't get around though is being able to control the size of the fonts in the Firefox menu?  I tried in vain with the FF available via the Package Manager, then I uninstalled it & installed directly from the Mozilla site, & still have the same problem.

I run 1280x1024 screen res', I'm using 24 minumum size fonts, which work everywhere except on the FF menus, tabs, address feilds.  Which is inconvenient.

I have modified the userChrome.css file, in a variety of ways & still no change in font size?


[I]/*
 * Make all the default font sizes 20 pt:
 */
  * {
    font-size: 24pt !important
  }
 
/*
 * Make menu items in particular 15 pt instead of the default size: 
*/
 
  menupopup > * {
    font-size: 24pt !important
  }
 

/* Make menus big, pretty and readable (like the old SGI look):
 * menubar isn't used after 12/19 builds, but is needed for NS6;
 * the rest are for post-12/19
 */
menubar, menubutton, menulist, menu, menuitem {
  font-family: helvetica !important;
  font-style: italic !important;
  font-weight: bold !important;
  font-size: 4mm !important;
}[/I]


Does anyone have a solution to this quirk?

---

### Post by handy on 2007-10-22
It did work! :-D

I had restarted FF to test each of the changes to the ***userChrome.css*** file; believing that I had not solved the problem I started this thread.

Anyway, I just restarted FF & the previously unresponsive small fontsizes are now all as they should be.  My eyes are very happy about this result.

Anyone who has a similar problem should look here for simple instructions with examples:

***_[http://www.mozilla.org/unix/customizing.html#usercss](http://www.mozilla.org/unix/customizing.html#usercss)_***

---

