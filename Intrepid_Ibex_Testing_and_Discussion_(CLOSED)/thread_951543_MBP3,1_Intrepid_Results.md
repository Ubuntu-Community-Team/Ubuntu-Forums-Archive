---
title: "MBP3,1 Intrepid Results"
date: 2008-10-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by trouble1313 on 2008-10-18
I didn't find much discussion about Intrepid here so I figured I'd post my findings thus far:

Nvidia Driver- Working

Sound- Working

Network- Working with athk9. In fact working the best I've had it work ever outside of using ndiswrapper! Still not perfect, but good. Definitely weaker signal reception than under Windows or MacOS. WPA and WEP working. 

iSight- Working

Screen Brightness/Keyboard backlight- Not working. Can't be adjusted with pommed or brightness applet

Trackpad- Working- don't forget to change your xorg.conf synaptics setting from 'multifingerbutton' to 'clickfingerbutton' if you use multi-finger clicks. Took me a bit to track that one down ;)

Power use- Pretty good! I think once we can adjust brightness, this will be very battery efficient! 

So out of the box, everything seems good other than the backlight and keyboard lighting. I dig it!

-Trouble

---

### Post by kosumi68 on 2008-10-18
Great! Here are some earlier findings for Intrepid: [http://ubuntuforums.org/showthread.php?t=904508](http://ubuntuforums.org/showthread.php?t=904508). The lcd/kbd backlight issue has several problems with HAL attached to it, see [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/226894), [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/125918), and the recent thread [http://ubuntuforums.org/showthread.php?t=951477](http://ubuntuforums.org/showthread.php?t=951477). A solution exists, but it takes (too long) time to get it through...

---

### Post by trouble1313 on 2008-10-18
Kosumi,
   Thanks greatly for the pointers. I hadn't looked that far back for Intrepid threads (I must be getting old, I'm sooo behind the times just starting at beta ;) ). Now I at least can hop out to a vt and turn down the screen brightness to save some electrons. Not ideal, but workable until that fix swims downstream to me. Honestly I can live with it for a bit as long as ath9k continues to be kind!

-Trouble

---

