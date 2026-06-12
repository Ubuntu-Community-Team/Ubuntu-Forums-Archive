---
title: "State of Karmic Alpha and Booting..."
date: 2009-09-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by sports fan Matt on 2009-09-22
Since I had to reformat using Jaunty..im wondering if the black screen (aka booting via chroot) with the latest alpha is fixed.  Im running a a Lenovo IdeaCenter K Series K2.3  Pentium dual-core E2180(2.00GHz) 3GB DDR2 500GB Intel GMA 3100 Desktop.  I just have pics in my pictures folder (but can also be replaced via FB) (they're stored there as well)..Ideas?

---

### Post by VMC on 2009-09-22
All that chroot nonsense was from last week. It's all fixed now including the udev boot up errors. There's been a lot of updates since the black screen+chroot.

---

### Post by exploder on 2009-09-22
Is the problem with having to manually run fsck on boot up fixed?

---

### Post by kansasnoob on 2009-09-22
All seems well here, but I'm using legacy grub. I doubt that makes much difference, but thought I should mention it.

---

### Post by sports fan Matt on 2009-09-22
Im gonna give it a go..EDIT: was on vacation all last week, spent quality time with the mrs so wasn't around the pc much.

---

### Post by maheshasolkar on 2009-09-22
I still get black screen on my laptop, but it is because of an unrelated KMS+intel 855GM issue. My computer boots if I provide the 'nomodeset' parameter on the boot line in grub. Get a black screen if 'nomodeset' is not used.

---

### Post by ELD on 2009-09-22
If there are still major issues it will be fixed in a day or two for the run up to the beta no doubt :)

---

### Post by eluminx on 2009-09-22
> **exploder said:**
> Is the problem with having to manually run fsck on boot up fixed?

i think this issue is not fixed yet, i am still having trouble with it, on a fresh install and updates applied.  But like someone mentioned give it a day or 3 and it'll be fixed.

---

### Post by psyke83 on 2009-09-22
> **maheshasolkar said:**
> I still get black screen on my laptop, but it is because of an unrelated KMS+intel 855GM issue. My computer boots if I provide the 'nomodeset' parameter on the boot line in grub. Get a black screen if 'nomodeset' is not used.

Just a heads up, the Intel driver is Karmic is very slow with 855GM chipsets due to [this]("https://bugs.freedesktop.org/show_bug.cgi?id=22877") bug. If you find your 2D rendering slows significantly after a few minutes, I suggest* you try the [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") drivers, as the bug is fixed in the latest version of the driver.

I also always keep KMS disabled, as it doesn't initialize XV properly (and sometimes causes a hang on boot).

*Only if you're prepared to deal with X breakage, and keep a backup of working drivers ;).

---

### Post by cb951303 on 2009-09-22
> **VMC said:**
> All that chroot nonsense was from last week. It's all fixed now including the udev boot up errors. There's been a lot of updates since the black screen+chroot.

I'm still getting udev errors

---

### Post by ELD on 2009-09-23
Like i said guys give it a few days not a few hours...

---

### Post by maheshasolkar on 2009-09-23
> **psyke83 said:**
> Just a heads up, the Intel driver is Karmic is very slow with 855GM chipsets due to [this]("https://bugs.freedesktop.org/show_bug.cgi?id=22877") bug. If you find your 2D rendering slows significantly after a few minutes, I suggest* you try the [xorg-edgers]("https://launchpad.net/~xorg-edgers/+archive/ppa") drivers, as the bug is fixed in the latest version of the driver.

I also always keep KMS disabled, as it doesn't initialize XV properly (and sometimes causes a hang on boot).

*Only if you're prepared to deal with X breakage, and keep a backup of working drivers ;).

Thanks. In fact, I have been using the xorg-edgers drivers lately. They seem to be working good right now.

---

### Post by maheshasolkar on 2009-09-23
I was waiting for LP bugs [#392039]("https://bugs.launchpad.net/bugs/392039") and [#431812]("https://bugs.launchpad.net/bugs/431812") to be fixed. I think they should fix my situation with Intel video and KMS. Looks like they both have been fixed recently! I guess I'll find out once I get to my test laptop!

---

