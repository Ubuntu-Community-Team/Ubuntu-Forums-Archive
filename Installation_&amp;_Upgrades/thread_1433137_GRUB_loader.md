---
title: "GRUB loader?"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by [Shadow] on 2010-03-18
I reinstalled karmic koala inside of windows and then rebooted as instructed. It booted up into ubuntu to complete the installation again. The next time i restart after the operating is fully installed It goes to a GRUB terminal type thing. Why wont it boot KArmic like normal?

---

### Post by z_diver on 2010-03-18
In Grub2 on 9.10 there exists a "feature" whereby if grub only has one OS it will boot it directly without going to a grub menu list first.  However, if there are 2 or more OSs it will show the list in order for you to choose one.  

If that is not what you are seeing, and you are actually getting to a login prompt, I would think that your xorg config is not working properly.  There are several well documented ways to reinstall xorg without reinstalling the OS so let us know if that's what you think it is.

---

### Post by phillw on 2010-03-18
> **'[Shadow] said:**
> I reinstalled karmic koala inside of windows and then rebooted as instructed. It booted up into ubuntu to complete the installation again. The next time i restart after the operating is fully installed It goes to a GRUB terminal type thing. Why wont it boot KArmic like normal?

Is it the dreaded ```
sh: grub>
```

If it is, I'd head over to [http://www.ubuntuforums.org/showthread.php?t=1314064&page=10](http://www.ubuntuforums.org/showthread.php?t=1314064&page=10)

That points to a bug in grub2 that affects wubi, and the work round

If you still have problems, pop a note onto that thread, it does get looked at.

Regards,

Phill.

---

### Post by [Shadow] on 2010-03-19
thanks for the help guys...

---

