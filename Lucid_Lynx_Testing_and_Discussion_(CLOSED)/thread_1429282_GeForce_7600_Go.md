---
title: "GeForce 7600 Go"
date: 2010-03-13
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by azhtar on 2010-03-13
Hi, I have a big issue here, I don't know why when I try to boot from USB (i'm trying to do a fresh install BTW) when X starts everything looks like garbage so I can't do anything so, what can I do? Is there a way that I can install propiertary drivers right into the ubuntu setup image?

I guess it has something to do with the new nvidia driver

---

### Post by MacUntu on 2010-03-13
Try booting with the "nomodeset" option enabled (IIRC it's in the F6 "Other options" menu).

---

### Post by vishalrao on 2010-03-13
Yes, possibly related to my issue too: [http://ubuntuforums.org/showthread.php?t=1428752](http://ubuntuforums.org/showthread.php?t=1428752)

I use "nouveau.modeset=0" which seems to work. (Also ensure I dont set gfxpayload or vga options).

---

### Post by azhtar on 2010-03-26
> **MacUntu said:**
> Try booting with the "nomodeset" option enabled (IIRC it's in the F6 "Other options" menu).

Dude you totally made my day, that was the answer to my problem.

I totally forgot to give feedback

---

