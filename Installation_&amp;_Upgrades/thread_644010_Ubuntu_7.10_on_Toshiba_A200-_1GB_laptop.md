---
title: "Ubuntu 7.10 on Toshiba A200- 1GB laptop"
date: 2007-12-18
forum: Installation &amp; Upgrades
---

### Post by peterpan168 on 2007-12-18
I have just installed Ubuntu on my laptop referenced in the title of the topic, but I think there is some incompatibility with the graphics card ATI Mobility HD2600, because I do not see the loading screen of ubuntu (appears just a black screen), and then appears the login windows with no problems. Then, when I chagne some configuration of the graphics card the colors get messy, I do not see a thing.

Can you help me, please? I would love to use Ubuntu more regurlalrly. Thank you.

---

### Post by logos34 on 2007-12-18
this might help:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Fix_Slow_boot.2Ffaulty_splash_screen)

---

### Post by peterpan168 on 2007-12-18
It did not work. Sorry. :(

---

### Post by logos34 on 2007-12-18
is the restricted (graphics) driver enabled?

---

### Post by logos34 on 2007-12-18
there's another tip at the bottom of the page link I gave you:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_change_the_USplash_Screen_on_startup.2Fshutdown)

---

### Post by peterpan168 on 2007-12-18
What is the restrcted graphics driver?

That did not work too.

I can't even enable the desktops effects. There should be an incompatability with my graphics card, since it is good enough for that.

---

### Post by logos34 on 2007-12-18
System>Admin.>restricted drivers manager>enable

---

### Post by Jorin on 2008-01-04
I'm having a similar problem with my Satellite a200. I'm getting video, but not at the laptop's full resolution of 1280x800. I went to restricted drivers, but I got a prompt saying "you do not need restricted drivers." I think I do though, to get the most out of my video card.

---

### Post by Jorin on 2008-01-04
> **Jorin said:**
> I'm having a similar problem with my Satellite a200. I'm getting video, but not at the laptop's full resolution of 1280x800. I went to restricted drivers, but I got a prompt saying "you do not need restricted drivers." I think I do though, to get the most out of my video card.

Update: 

Got past that step by finding the ATI catalyst drivers for linux and installing the package. The display is a bit garbled (colours are all wrong on the desktop) but I'll plug away at that and see what I can do.

---

