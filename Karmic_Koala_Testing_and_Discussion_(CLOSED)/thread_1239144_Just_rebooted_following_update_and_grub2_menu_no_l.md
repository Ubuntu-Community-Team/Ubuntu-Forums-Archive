---
title: "Just rebooted following update and grub2 menu no longer appears."
date: 2009-08-13
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by philinux on 2009-08-13
Just boots up to gdm.

---

### Post by artir on 2009-08-13
It's part of the new boot experience.
Don't worry, they are working on the new OS chooser

---

### Post by plun on 2009-08-13
Just press "Esc" directly and you will see the Grub menu

---

### Post by philinux on 2009-08-13
Ah! thanks guys. Just did major update after 6 days away on hols and being forced to use xp machines. Arrrggghhh.

[edit] the devel-announcement email ended up in my junk folder by mistake doh.

---

### Post by autocrosser on 2009-08-13
Look in my theming thread--info to re-enable menu is there....

Here you go mate---```
If you're upset by the boot menu being hidden all of a sudden, then you 
should edit /etc/default/grub, comment out the GRUB_HIDDEN_TIMEOUT line, 
and set GRUB_TIMEOUT to the timeout you want in seconds (say "10"), then 
run 'sudo update-grub'. 
```

---

