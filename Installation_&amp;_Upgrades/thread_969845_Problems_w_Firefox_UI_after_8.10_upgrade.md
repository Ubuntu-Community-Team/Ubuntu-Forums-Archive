---
title: "Problems w/ Firefox UI after 8.10 upgrade"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by MystaMax on 2008-11-03
I have a laptop where I upgraded 8.04 64-bit to 8.10 64-bit, using update-manager -d. During the upgrade, I was running Firefox, which some believe is causing further problems.

In Firefox, I tried editing the toolbar area (right-click -> Customize), and restoring default set, but it looks the same. I tried deleting the localstore.rdf, and restarting Firefox, but that didn't work, results were the same.

My fix was to disable the Ubuntu Firefox Modifications extension. With a name like, "Ubuntu Firefox Modifications", you would think its a necessity. But, I've yet to come across any issues while its disabled. This was the only way I could edit my Firefox UI. 

**What exactly does this extension do? Is it a necessity?** I've read its needed to update Firefox properly, can someone help me confirm this? Here's a list of things I read its needed for:

• It allows users to install Firefox add-ons through the Ubuntu package manager. [http://bit.ly/1t026c](http://bit.ly/1t026c)
• its just there to modify Firefox to fit in w/ gnome. [http://bit.ly/1t026c](http://bit.ly/1t026c)
• helps the update process. [http://bit.ly/1t026c](http://bit.ly/1t026c)

I'm not sure, but I'd like to know. I've provided screenshots, and links to articles I found relevant.

**Update**: It seems pages w/ flash are locking the browser up. I can't determine if this is from disabling the Ubuntu Firefox Modifications extension, but pages that do have flash, lock the browser for about 30 seconds, and then return.
[B]
Update 2[/B]: I'm honestly not sure how I had flash installed previously. I know it was a 10.0 release, but it could of been a RC. I removed the old version (sudo rm -f /usr/lib/mozilla/plugins/libflashplayer.so) and installed the latest from the repositories (sudo aptitude install flashplugin-nonfree). All my browser lockups are gone! 
[B]
Links[/B]
corrupt localstore.rdf - [http://bit.ly/Gh5uQ](http://bit.ly/Gh5uQ)
Multiple instance of buttons - [http://bit.ly/Pg1ww](http://bit.ly/Pg1ww)
cannot customize Firefox after upgrade - [http://bit.ly/2cfB1w](http://bit.ly/2cfB1w)

---

### Post by dgibsonky on 2008-11-04
Your Flash reinstallation appears to have worked for me, as well...thanks very much!

---

