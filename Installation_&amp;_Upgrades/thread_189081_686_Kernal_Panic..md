---
title: "686 Kernal Panic."
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Omnios on 2006-06-04
Hi I just installed 6.06 and desided to intall the 686 packages with the headers etc but am getting the following error when trying to boot with the 686 kernal.
```
Kernal Panic : VFS : unable to root fs on 03:41
```
 Im not shure if it a grub thing or something else, anyone have any suggestions.

---

### Post by jbrader on 2006-06-04
Are you sure you installed the 2.6 kernal?  I accidently installed 2.4 the other day and got the same thing, after I went back and changed to 2.6 all was well.

---

### Post by John.Michael.Kane on 2006-06-04
Omnios I beleave that error means it it cannot find your root (/) directory to boot from.  being that i never had this show up on my installs it hard for me to give a fix for it.

Sidenote: If you still have to old kernel still installed try booting from it.

---

### Post by Omnios on 2006-06-05
You where right it was the wrong kernal, all fixed now.

---

### Post by jbrader on 2006-06-06
I'm glad to hear it all worked out.

---

