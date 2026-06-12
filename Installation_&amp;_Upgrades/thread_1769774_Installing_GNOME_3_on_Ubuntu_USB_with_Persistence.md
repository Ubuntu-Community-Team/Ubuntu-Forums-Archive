---
title: "Installing GNOME 3 on Ubuntu USB with Persistence"
date: 2011-05-28
forum: Installation &amp; Upgrades
---

### Post by C4Reaper on 2011-05-28
Title says everything.
I want to install GNOME3 on Ubuntu 11.04 LiveUSB using persistence mode, but when I did that (following the PPA-thingy rules) it says no root folder can be defined. ignored. says restart system to complete updates, when I did and selected my USB from boot menu it would just blink for a few secs and give me the 
'starting windows' animation. I did that twice to make sure there is absolutely no room for mistake, still no luck. any help?

BONUS: is there some way to modify the installation files to make it GNOME 3 right out of the box?

OFFTOPIC BONUS: is there another way to make it skip the Install Ubuntu/Try Ubuntu screen and just run the [CENSORED] UI?

Cheers :)

---

### Post by Herman on 2011-06-11
You could try making a regular Ubuntu installation in your USB flash memory stick if it's large enough, say 8 or 16 GB.

---

### Post by linuxinstalledfromhdd on 2011-06-11
> **C4Reaper said:**
> Title says everything.
I want to install GNOME3 on Ubuntu 11.04 LiveUSB using persistence mode, but when I did that (following the PPA-thingy rules) it says no root folder can be defined. ignored. says restart system to complete updates, when I did and selected my USB from boot menu it would just blink for a few secs and give me the 
'starting windows' animation. I did that twice to make sure there is absolutely no room for mistake, still no luck. any help?

BONUS: is there some way to modify the installation files to make it GNOME 3 right out of the box?

OFFTOPIC BONUS: is there another way to make it skip the Install Ubuntu/Try Ubuntu screen and just run the [CENSORED] UI?

Cheers :)

Here is what I would do if that is what I wanted to create..

First I would start with a fresh minimal installation of ubuntu from the ubuntu alternative disc..  Then I would install Gnome 3 from the PPA.  I would fine tune my OS to get it to be -exactly- the way I wanted it to be.  Then I would install Remastersys:

[http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/](http://cinderbox.net/2011/06/02/creating-custom-ubuntu-live-usb-with-remastersys/)

And then I would take the ISO remastered OS and use Startup Disc Creator and select the persistence mode I wanted to add.

It really doesn't get much easier than that, that is -if- you can get Gnome 3 working for you.

---

