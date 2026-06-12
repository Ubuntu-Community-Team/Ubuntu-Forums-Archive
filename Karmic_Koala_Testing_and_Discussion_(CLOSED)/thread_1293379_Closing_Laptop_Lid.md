---
title: "Closing Laptop Lid"
date: 2009-10-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bren21 on 2009-10-17
In Karmic there is no option for Do Nothing in power settings when you close the laptop lid. I connect my laptop to my tv to watch movies and I don't want to be able to see my laptop screen too. Why was this removed? Is there any way to make the screen do nothing again?

---

### Post by Seq on 2009-10-17
> **bren21 said:**
> In Karmic there is no option for Do Nothing in power settings when you close the laptop lid. I connect my laptop to my tv to watch movies and I don't want to be able to see my laptop screen too. Why was this removed? Is there any way to make the screen do nothing again?

Hi, I see an option for "Blank Screen". Does this blank your secondary output as well as the LVDS screen buint-in? If so, this should be filed as a bug.

---

### Post by bren21 on 2009-10-17
Yes, this blacks out my tv monitor as well.

---

### Post by happyhamster on 2009-10-17
In a terminal type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes). Good luck.

Weird thing is that after setting it in gconf, the "Do nothing" option appears in the preferences menu again.

---

### Post by Seq on 2009-10-17
Be sure to file a bug for the blank screen option as well. The blank screen on lid closed option should only blank the LVDS screen (the one being closed)

---

### Post by happyhamster on 2009-10-17
> **Seq said:**
> Be sure to file a bug for the blank screen option as well. The blank screen on lid closed option should only blank the LVDS screen (the one being closed)
See:
[https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/390816](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/390816)

---

### Post by bren21 on 2009-10-17
> **happyhamster said:**
> In a terminal type: gconf-editor

Navigate to apps-->gnome-power-manager-->buttons and set lid_ac and/or lid_battery to "nothing" (without the quotes). Good luck.

Weird thing is that after setting it in gconf, the "Do nothing" option appears in the preferences menu again.

Awesome, works perfectly. Thanks a lot.

---

