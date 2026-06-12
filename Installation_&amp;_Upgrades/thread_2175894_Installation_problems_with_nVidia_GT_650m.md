---
title: "Installation problems with nVidia GT 650m"
date: 2013-09-21
forum: Installation &amp; Upgrades
---

### Post by jackdneilson on 2013-09-21
Hi all,

So i'm a total noob when it comes to ubuntu, when I try and install it on my laptop I get a purple splash screen, an underscore flashing a few times and then the screen goes completely black (with no backlight). I think the problem is with the graphics card, which is apparently not supported. I came across bumblebee, however I can't use it because I can't install ubuntu. Any help on this would be greatly appreciated. The version i'm trying to install is 12.04 and the graphics card is an nVidia GT 650m.

EDIT: I also have an intel i5, so i'd assume intel integrated graphics? I'm really not sure at this point.

Many thanks,
Jack

---

### Post by papibe on 2013-09-21
Hi jackdneilson. Welcome to the forums ):P

It may be a graphic card compatibility problem. I would try to boot using the **nomodeset** option. Check the section 'How to temporarily set kernel boot options on an installed OS' in this [thread]("http://ubuntuforums.org/showthread.php?t=1613132") for details.

If that works, follow the steps on the next section (How to permanently set kernel boot options on an installed OS) in order to set the option for every subsequent boot.

Hope it helps. Let us know how it goes.
Regards.

---

