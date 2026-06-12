---
title: "Reverting to Firefox 2 in Hardy"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by theoutdoors on 2008-04-27
Hi,

I found I needed, for the time being, to revert back to Firefox 2 instead of 3b5 as my bank currently block Firefox 3. In case it helps anyone else, this is what I did to do so:

1. Completely removed all firefox related packages in synaptic.

2. _Sorting out add on problems_

I had previously installed adblock plus and noscript in firefox 3 and on my first attempt to go back to firefox 2, I found ff2's add ons were broken (It wouldn't let me add or remove any). I think this is because the .mozilla directory for ff3 is different than for ff2. So, I deleted my .mozilla directory (rm -r .mozilla). Note: I'm not up on exactly what is stored in .mozilla but I suspect you might lose your bookmarks etc by deleting it. I wasn't worried about losing anything though.

3. Installed firefox-2, firefox-2-gnome-support, ubufox, totem-mozilla and flashplugin-nonfree packages using synaptic.

4. _Sorting Out Fonts_

I found the fonts to be small and not very readable compared to ff in gutsy. To improve this I went, in ff2, to edit->preferences->content and selected the default font to be 'serif'. This seems to get fonts back to being similar to how they were for me in ff in gutsy. I'm not certain whether they're exactly the same or not though.

5. _Fixing launch icon in gnome top panel_

To sort out the launch icon, I right clicked it then selected properties and put the following details in the boxes:

Type: Application
Name: Firefox Web Browser
Command: firefox-2 %u
Comment: Browse the World Wide Web

I didn't need to find the icon graphic as it sorted that out by itself.

Hopefully that will help someone. There are probably better ways to do some bits but the above seems to be OK for me. If it wasn't for needing ff2 for my bank I would probably have stayed with ff3b5 though!

---

### Post by raul_ on 2008-04-27
You should add a [HOW TO] to your post title :)

---

