---
title: "New wave firefox not right"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ELD on 2009-03-27
In the top menu firefox has black writing, everything else seems to use white, it is highly annoying!

Shot is attached

---

### Post by taavikko on 2009-03-27
This issue is been reported, 
[https://bugs.edge.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/347691](https://bugs.edge.launchpad.net/ubuntu/+source/gnome-themes-ubuntu/+bug/347691)

Please change status to confirmed, rather than just commenting.

---

### Post by ELD on 2009-03-27
That is different, that is about the bookmark utility, i am talking about the general menu along the top like my screenshot shows comparing it to nautilus.

---

### Post by philinux on 2009-03-27
Fine here. Using new wave and dark menus.

---

### Post by ELD on 2009-03-27
Well my screenshot of new wave looks completely different so something is up.
Yours is even different to the bug report posted ealier -> [http://launchpadlibrarian.net/24301561/Screenshot.png](http://launchpadlibrarian.net/24301561/Screenshot.png)

Your top menu is different to ours.

BTW -> fresh install via beta live cd.

---

### Post by philinux on 2009-03-27
I assume you've double checked settings in appearance>customize>window border.

Mine is updated from alpha2 > beta. With breakage along the way. What fun.

---

### Post by taavikko on 2009-03-27
> **ELD said:**
> That is different, that is about the bookmark utility, i am talking about the general menu along the top like my screenshot shows comparing it to nautilus.

Should be the same, since new wave fails to install .css to firefox settings,
which overrides layout settings colors, fonts and such)

But then again, might be wrong :)

---

### Post by ELD on 2009-03-27
> **philinux said:**
> I assume you've double checked settings in appearance>customize>window border.

Mine is updated from alpha2 > beta. With breakage along the way. What fun.

Like i said it is a fresh beta install, i have checked and it is set to new wave, everything is on new wave, so it seems the beta cd has a duff version of it.

---

### Post by smartboyathome on 2009-03-27
> **ELD said:**
> Like i said it is a fresh beta install, i have checked and it is set to new wave, everything is on new wave, so it seems the beta cd has a duff version of it.

New Wave requires its own Firefox settings to get it to work around the Firefox bugs. These aren't installed by default.

---

### Post by ELD on 2009-03-27
Well i never saw any mention of that anywhere? That is pretty annoying.

---

### Post by bekind2thenoob on 2009-03-27
If you download the newwave pack from here [https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/NewWave)

it contains a hack to fix the firefox menus among other goodies.
Openoffice has the same problem, no fix for that though (both are fine in the darkmenues version of the theme though). Hopefully it'll be fixed in the 0.8 release.

Instructions on installing the fix for ff are in the included readme btw.

---

### Post by ELD on 2009-03-27
I am on jaunty not intrepid though, your link was to intrepid?

Which readme are you talking about, i didn't know there was a readme for themes included in the defualt install heh.

---

### Post by smartboyathome on 2009-03-27
> **ELD said:**
> I am on jaunty not intrepid though, your link was to intrepid?

Which readme are you talking about, i didn't know there was a readme for themes included in the defualt install heh.

That will work for Jaunty. The readme is in the package for NewWave on the page linked.

---

### Post by dilomo on 2009-03-27
Don't bother installing fixes. Just download the theme I have posted [  here (LaunchPad)  ]("https://bugs.launchpad.net/anton/+bug/335496") and you'll have no problems. Search for newwave-FF-02.jar file.

P.S. I'm still fighting with OOs but it seems that this could not be fixed. Will have to use the dark menus version if you can't stand the menus.

P.P.S. The theme in Jaunty Beta should be version 0.8.0.

---

### Post by bekind2thenoob on 2009-03-27
Its the themes wiki page it hapens to be on the intrepid wiki site.

The themes New Wave, Dust and Dust Sand are all created by community members and have been included in jaunty instead of some of the older gnome themes.

On the wiki page, towards the bottom there will be several download links for the **New Wave Pack** if you download the latest version (0.7.3) then extract the contents of the archive (right click on it and select extract here) you will find a the readme file in the folder which tells you how to install the firefox fix.

I think its named PLEASE README or something similarly attention grabbing lol

---

### Post by ELD on 2009-03-27
Thanks for the help i will see what i can do and report back, seems annoying the beta of jaunty can't include this fix :(

@dilomo where do i put the file you provided buddy? :D

---

### Post by dilomo on 2009-03-27
> **ELD said:**
> Thanks for the help i will see what i can do and report back, seems annoying the beta of jaunty can't include this fix :(

@dilomo where do i put the file you provided buddy? :D

Drag it into the themes tab of your Tools > Add-ons in firefox.

---

### Post by ELD on 2009-03-27
> **dilomo said:**
> Drag it into the themes tab of your Tools > Add-ons in firefox.

Works perfectly, thanks a lot buddy!

---

### Post by bekind2thenoob on 2009-03-27
It is a very nice ff theme nice work!!

---

### Post by philinux on 2009-03-27
I'm using "classic compact", takes up less real estate and is the same light grey background colour.

---

### Post by Stetzen on 2009-03-27
> **philinux said:**
> I assume you've double checked settings in appearance>customize>window border.

Mine is updated from alpha2 > beta. With breakage along the way. What fun.

It looks like you are using some custom theme for firefox.. The default theme tries to use the GTK look, and custom styles overwrite it.

---

### Post by philinux on 2009-03-27
> **Stetzen said:**
> It looks like you are using some custom theme for firefox.. The default theme tries to use the GTK look, and custom styles overwrite it.

Yes, classic compact. It use about a centimetre less vertically for the icons,toolbars etc and the bookmarks toolbar uses less space per bookmark.
Interesting the OP's menus appear as black text on the grey background. I've not seen that.

---

