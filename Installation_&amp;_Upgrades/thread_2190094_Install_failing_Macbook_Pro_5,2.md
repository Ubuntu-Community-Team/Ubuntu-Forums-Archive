---
title: "Install failing Macbook Pro 5,2"
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by khean on 2013-11-25
Hello,

I have tried and tried to install Ubuntu on my Macbook Pro 5,2 with no success.

Every time I try, I get to the purple screen with the battery + man then I get nothing but a black screen. The disc drive makes noise for about a minute and then nothing. 

I though that it was just taking time to read off the boot disc, so I left it overnight and still nothing.

I have tried every single tutorial I could find here on the forum and elsewhere. They've included various combinations of:

-Ubuntu 12.04 / 13.04 / 13.10 (32 and 64 bit)
-rEFIt/rEFInd
-Partition via Disk Utilities / gDisk in OS X terminal / Bootcamp

Every time, just a blank black screen, no "Try" or "Install" screen.


It is a matter of installing 9.10, then upgrading?

Any help would be greatly appreciated.

Thanks!

---

### Post by khean on 2013-11-26
After hours and hours I've finally figured out what the issue was, all thanks to this blog post: [http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/#comment-539](http://myhumblecorner.wordpress.com/2011/05/31/gentoo-and-a-little-ubuntu-on-a-macbook-pro-53/#comment-539)

"1. [COLOR=#000000][FONT=Arial]Boot into OSX, go to System Preferences -> Energy Saver, and select the high performance option (vs. the battery option). This turns on the fancy NVidia 9600M video card."

Boom. Working now. I didn't even have to add the nouveau.noaccel=1 boot option. (Although I did select it to 'nomodeset').

Happily rocking 13.04 with Gnome Shell 3.10.[/FONT][/COLOR]

---

