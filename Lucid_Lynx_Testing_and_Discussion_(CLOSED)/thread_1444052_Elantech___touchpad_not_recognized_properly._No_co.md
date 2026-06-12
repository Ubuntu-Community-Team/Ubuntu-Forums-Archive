---
title: "Elantech   touchpad not recognized properly. No configuration gui for touchpad."
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by timuckun on 2010-03-31
The elan technologies touchpad used by many Asus and some dell laptops is not recognized properly by Lucid. The "pointing devices" application recognizes it as imPS/2 logitech wheel mouse.

The multi touch works. Two finger and three finger taps work. Two finger scrolling also works but only on the vertical plane.

There is no way to adjust the sensitivity of the pad or to disable tap to click.

Lynx should support this popular option out of the box.

In the mean time does anybody have any suggestions as to how I can configure this? Gynaptics complains about the setting in xorg.conf. I have set up an FDI but it seems to have effect because presumably it's not a synaptics touch pad.

---

### Post by timuckun on 2010-04-03
> **timuckun said:**
> The elan technologies touchpad used by many Asus and some dell laptops is not recognized properly by Lucid. The "pointing devices" application recognizes it as imPS/2 logitech wheel mouse.

The multi touch works. Two finger and three finger taps work. Two finger scrolling also works but only on the vertical plane.

There is no way to adjust the sensitivity of the pad or to disable tap to click.

Lynx should support this popular option out of the box.

In the mean time does anybody have any suggestions as to how I can configure this? Gynaptics complains about the setting in xorg.conf. I have set up an FDI but it seems to have effect because presumably it's not a synaptics touch pad.

I hate to bump my own post but...

I am getting really desperate. What can I do to make this touchpad a little less sensitive or to disable tap click. I have been trying to follow some tips on other forums but so far no luck.

---

### Post by TheCowGod on 2010-04-28
See this post for the solution.

[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

---

### Post by timuckun on 2010-04-28
> **TheCowGod said:**
> See this post for the solution.

[http://ubuntuforums.org/showthread.php?p=9175201#post9175201](http://ubuntuforums.org/showthread.php?p=9175201#post9175201)

Wow. That's a drastic resolution. I'd have to apply the patches and rebuild the driver with every kernel update right?

Any clue as to when those patches will be in the kernel?

---

### Post by Bender2k14 on 2010-04-28
It looks like they could make version 2.6.34:
[http://www.spinics.net/lists/linux-input/msg08298.html](http://www.spinics.net/lists/linux-input/msg08298.html)

---

