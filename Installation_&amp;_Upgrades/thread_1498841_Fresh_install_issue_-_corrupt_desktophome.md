---
title: "Fresh install issue - corrupt desktop/home?"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by phazon. on 2010-06-01
Hi

I did a fresh install of 10.04 over 9.10. I have a separate /home partition, and during the install I designated this as the /home partition in the partition editor. The install completed without errors.

However, when I boot into 10.04, the desktop is not working correctly - windows do not have minimise, maximise and close icons, or a title bar - the top of the window is the menu bar. All windows open in the top left of the screen. It is as if some critical windowing component is not registered or something

This has now happened on a number of attempted installs.

Any ideas what is going on?

Thanks

---

### Post by nerdzero on 2010-06-01
Hi phazon,

Sounds like a corrupt saved session.  Clean out this folder:  ~/.config/gnome-session/saved-session

---

### Post by phazon. on 2010-06-01
Hi nerdzero

That seems to have done the trick - thanks alot, really appreciate the quick reply.

Cheers

---

