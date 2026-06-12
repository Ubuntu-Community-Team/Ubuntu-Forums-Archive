---
title: "Can I still use 9.04 Jaunty after I upgraded to 9.10 Karmic?"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by Aeric on 2009-12-17
Can I still see Jaunty listed in GRUB bootloader after I upgraded to Karmic using Update Manager? Meaning that can I have both Jaunty and Karmic sharing the same partition and swap partition? Let say I upgraded to Karmic but it got problem that I need to reverse back to Jaunty.

---

### Post by SlugSlug on 2009-12-17
nope

---

### Post by Aeric on 2009-12-17
Thanks for the answer. :)

---

### Post by efflandt on 2009-12-18
You may still have your old Jaunty kernel from before the upgrade, and that should be able to boot.  But everything will visibly appear to be Karmic, and sound may not work with the older kernel.

The reason I know that is because I just discovered Ubuntu a week before 9.10 was released, and then upgraded both my desktop and laptop from 9.04.  Initially I was getting opps in the new 64-bit kernel for something that really should have been ignored, and when using the old kernel, I had no sound.   Since launchpad was swamped with unnecessary bug reports, the cure in an update was to disable "apport" by default, and just manually enable it if you need to report a real bug.

---

