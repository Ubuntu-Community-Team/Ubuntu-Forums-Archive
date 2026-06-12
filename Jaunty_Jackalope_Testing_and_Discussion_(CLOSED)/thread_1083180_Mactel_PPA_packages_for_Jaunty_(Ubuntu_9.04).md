---
title: "Mactel PPA packages for Jaunty (Ubuntu 9.04)?"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by gotgenes on 2009-02-28
I was trying out the Alpha 5 release of Jaunty on my MacBook 5.1 and when it came time to installing packages from the Mactel PPA, I found they weren't actually available. Are these packages not yet being built for Jaunty? My suspicion is that they're not. On the other hand, some things were working out of the box--the iSight camera, for example.

---

### Post by cyberdork33 on 2009-02-28
> **gotgenes said:**
> I was trying out the Alpha 5 release of Jaunty on my MacBook 5.1 and when it came time to installing packages from the Mactel PPA, I found they weren't actually available. Are these packages not yet being built for Jaunty? My suspicion is that they're not. On the other hand, some things were working out of the box--the iSight camera, for example.
The iSight works out of the box depending on the hardware... not the version of linux.

To my knowledge, no packages have been built for jaunty. What specifically are you trying to use? (i.e. what is not working?)

---

### Post by gotgenes on 2009-03-03
> **cyberdork33 said:**
> To my knowledge, no packages have been built for jaunty. What specifically are you trying to use? (i.e. what is not working?)
I'm looking for support for the backlight keys for the display and the keyboard, most importantly. For other things (e.g., sensors), I don't know. It would help to have a list of what packages from the Mactel PPA are no longer necessary in Jaunty, because they have been included in the kernel, HAL, etc. shipping with Jaunty.

---

### Post by inphektion on 2009-03-03
when cyberdork posted that 2 days ago the PPA for jaunty had no packages.  Now thought you can install applesmc-dkms, mbp-nvidia-bl, and I even did isight firmware.

I too would like to know if i even need anyother packages for jaunty.  I still need sound, keyboard backlight, and don't have my touchpad working with right click.

---

### Post by cyberdork33 on 2009-03-03
there is no list, mainly because none of us really know without scouring through changelogs. 

If it is not working in Jaunty, first, you should file a bug so that we can work toward not having to rely on a PPA in the future. You can check the Intrepid wiki page to see what package fixed this issue there, and use that to determine the package to file the bug against. 

I think the sound issues haven't been solved yet (even with the PPA).

the backlight was fixed with hal-applesmc package I believe, and I think this package may been in the repos now. 

I barely started using a Mac laptop with Ubuntu recently, and I haven't quite figured the touchpad config out yet myself. It doesn't seem to load the options in my fdi file.

and yes, there are some jaunty packages now.

---

### Post by gotgenes on 2009-03-04
> **cyberdork33 said:**
> If it is not working in Jaunty, first, you should file a bug so that we can work toward not having to rely on a PPA in the future. You can check the Intrepid wiki page to see what package fixed this issue there, and use that to determine the package to file the bug against.
Done. See [this thread]("http://ubuntuforums.org/showthread.php?p=6838533").

---

