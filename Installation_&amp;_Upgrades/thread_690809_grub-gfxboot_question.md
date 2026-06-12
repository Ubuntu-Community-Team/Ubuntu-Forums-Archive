---
title: "grub-gfxboot question"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Haluci on 2008-02-07
I just recently installed grub-gfxboot (following the instructions in [this post]("http://ubuntuforums.org/showthread.php?t=208855")).  It works fine, except it doesn't load the theme I've told it to.  Here's my menu.lst:

```
gfxmenu /boot/grub/message.blusplash
default 0
fallback 1
timeout 10
```

Which is followed by my partitions which I'll post if they're relevant.

So, when my system boots, I just get the default grub look without any splash.  I'm wondering if I am doing something wrong, whether the syntax is wrong or there's something wrong with my splash file.  Thanks for the help in advance!

---

### Post by Haluci on 2008-02-08
bumping after 4 hours of inactivity.  If this is the wrong forum for this kind of question, let me know.

---

### Post by bwtranch on 2008-02-08
Usually you should wait 24 hrs. before bumping. Maybe you didn't make it clear what you are asking.

---

### Post by Haluci on 2008-02-08
Never mind, I figured it out.  Apparently, you can't use a password with grub-gfx for some reason. :confused:

---

