---
title: "Rearranging panel icons in Karmic?"
date: 2009-07-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by thezood on 2009-07-29
I'm not yet sure if I'll be able to test the Alphas of Karmic, so I'll just go ahead and ask you about this bug I have found incredibly annoying: the problem that panel icons rearranges themselves when changing resolution ([https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/44082)).

Is it still present in Karmic?

---

### Post by dinxter on 2009-07-29
i know the one you mean :) theres no problem here with either a nouveau or a nvidia driver. the only way i can get this bug nowadays is when nvidia-settings is installed. this causes the desktop to be automatically set to 1024x768 when its actually supposed to be 1280x1024. as a result on first log in the icons are re-arranged as per that bug. but i would stress, only with nvidia-settings installed and only on a first log in, after that icons are fine on resolution changes

---

### Post by dinxter on 2009-07-29
just to add, the problem with nvidia-settings was caused by an old .config/monitors.xml file, removing that gets rid of the gnome/nvidia resolution mismatch.
so, no problems with icon placing on resolution change with either drivers at all. hopefully it'll be the same for you

---

### Post by thezood on 2009-07-29
Well, the million dollar question has to be if it's solved for us Intel users as well, since we don't use any nvidia stuff. :) As I understand it from the error report, the bug is in gnome-panel. Or am I wrong?

---

