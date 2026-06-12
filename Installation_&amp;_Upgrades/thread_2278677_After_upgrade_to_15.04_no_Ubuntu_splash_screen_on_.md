---
title: "After upgrade to 15.04 no Ubuntu splash screen on startup?"
date: 2015-05-18
forum: Installation &amp; Upgrades
---

### Post by egruber on 2015-05-18
No problems, just a minor question.  With prior versions, my laptop showed the word Ubuntu with dots underneath that turned purple/black as the laptop booted up.  Showed the same when powering down.  After 15.04, I no longer see it on bootup, but I noticed if I hit the left arrow key it comes back.  Just curious why this is.

---

### Post by dino99 on 2015-05-18
that is 'plymouth' splash screen, usually activated/deactivated into /etc/default/grub (quiet splash)

> sudo dpkg-reconfigure plymouth

---

### Post by egruber on 2015-05-18
Thanks, but it wasn't clear to me what steps I should take.  I did look in that grub file and it says GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

I also executed the sudo line you provided but it didn't change anything.

What was I supposed to do next?

---

