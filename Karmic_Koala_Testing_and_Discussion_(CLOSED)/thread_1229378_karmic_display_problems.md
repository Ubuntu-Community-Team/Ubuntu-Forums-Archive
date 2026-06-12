---
title: "karmic display problems"
date: 2009-08-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Kreuger on 2009-08-02
So because of the problems with the Intel i915 drivers (on my laptop) in Jaunty, I decided to upgrade to the Koala. However, upon loading the gdm my screen is pushed off to the right side of the screen and then continues on to the left. So my screen shakes all the time, however I am able to login. This also happens on the desktop every few seconds it will shake. After installing earlier, it eventually corrected itself however after rebooting the problem persisted. Im not sure if I have a setting wrong of if this is a bug I should put into Launchpad? My laptop is an IBM Thinkpad X30, using Xubuntu 9.10 and kernel 2.6.31-4 (generic).

---

### Post by VMC on 2009-08-02
> **Kreuger said:**
> So because of the problems with the Intel i915 drivers (on my laptop) in Jaunty, I decided to upgrade to the Koala. However, upon loading the gdm my screen is pushed off to the right side of the screen and then continues on to the left. So my screen shakes all the time, however I am able to login. This also happens on the desktop every few seconds it will shake. After installing earlier, it eventually corrected itself however after rebooting the problem persisted. Im not sure if I have a setting wrong of if this is a bug I should put into Launchpad? My laptop is an IBM Thinkpad X30, using Xubuntu 9.10 and kernel 2.6.31-4 (generic).

I was able to stop that "shaking" by using the "nomodeset" boot option. Mine has a "tearing" of the desktop if I don't use that option.

---

### Post by Kreuger on 2009-08-02
So when you get to grub, you edit the first line and just add nomodeset to the end?

---

### Post by ktp on 2009-08-02
> **Kreuger said:**
> So when you get to grub, you edit the first line and just add nomodeset to the end?

See this thread/comment:

[http://ubuntuforums.org/showpost.php?p=7719515&postcount=7](http://ubuntuforums.org/showpost.php?p=7719515&postcount=7)

---

### Post by Kreuger on 2009-08-03
Yeah, as I thought. Thanks

---

