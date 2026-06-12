---
title: "Installation of Karmic Koala with Grub &lt; 2?"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by night-wing on 2009-10-03
Hello.

I tried to install karmic koala on my notebook. This works and the notebook boots up with more performance as with intrepid or jaunty. But I have a problem with my imaging tool. I use "image for linux" to make images/backups of my harddisk. This tool can't backup and restore systems with grub 2 till now. But I don't want to change my used tool and switch to another. So my question is: Is there a way to install karmic with the "old" grub? If yes, how?

An update from jaunty or intrepid fails and leaves a flickering, not functional system. So a plain new installation is the only way for me.

Would be glad, if you could help me.

Thanks

nightwing

---

### Post by ranch hand on 2009-10-03
I am not on 9.10 right now but I believe that grub .97 (grub-legacy) is still in the repo.

If not you could enable the Jaunty repo (I believe it is in the "main") and download it from there and then get rid of that repo.

---

### Post by FuturePilot on 2009-10-03
grub-legacy is indeed still in the repos. There was a thread around here I think, about downgrading to grub-legacy. But I don't think it's possible to install it with grub-legacy, you'll have to manually downgrade it.

---

### Post by kansasnoob on 2009-10-03
Read all of my posts here:

[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

The steps you'll want to follow, assuming you've already installed Karmic w/grub2, are in post #16.

**[COLOR="Red"]But read all of my posts in that thread, especially the warnings![/COLOR]**

If you're at all unsure of anything ask questions here on the forums before proceeding!

Also, if Karmic is the only operating system on that machine be absolutely certain you have a working Ubuntu Live CD so we can mount and use chroot to fix Karmic if something breaks! It need not be a Karmic disc.

---

### Post by night-wing on 2009-10-05
Hello.
Thanks for the hint.
Seems to be very complicated. I think, I'll stay at intrepid.

---

